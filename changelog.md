This document covers the changes from the original khuedoan repo.

1. Changed most instances of `github.com/khuedoan/homelab` with `github.com/stevesaliman/homelab`.
   This had to be done carefully, because some of the references were to pull requests and other
   khuedoan repos.

2. Changed some instances of `khuedoan.com` to `saliman.net`, but only the ones that referred to 
   apps that would run on the cluster.  References to external documentation needed to stay the same.

3. Replaced `Asia/Ho_Chi_Minh` with `America/Denver`

4. Replaced `id_ed25519` with `id_rsa` and commented out the code in metal/Makefile that generates
   keys.  We can use our existing keys.

5. Added a cluster_name variable to the prod inventory, made a change to the k3s role to use it
   when creating the local kubernetes config file.

6. Made a prereq script to install prerequisites

7. Modified the configure script to replace the branch/tag of the repo that Argo will use when it
   deploys the apps.

8. Modified scripts to only export a kube config if I don't already have one.

9. Changed the "first run" detection in bootstrap.yml to use ingress-nginx instead of gitea because
   We probably don't need it.

10. Added reflector to the platform directory for secret syncing.

11. Changed the way cert-manager creates the certs.  I now have 
  `cert-manager/templates/root-cert-issuer` to issue a self-signed cert, 
  `cert-manager/templaces/root-certificate` to create the root certificate, and 
  `cert-manager/templates/clusterissuer.yaml` which uses a CA issuer to create certs with the 
  root certificate.  The root certificate is annotated with reflector annotations to sync it with
  the global-secrets.  Also changed the name of the certificate issuer in the apps that request
  certificates, so they request them from the right issuer.
