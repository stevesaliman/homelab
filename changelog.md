This document covers the changes from the original khuedoan repo.

1. Changed most instances of `github.com/khuedoan/homelab` with `github.com/stevesaliman/homelab`.
  This had to be done carefully, because some of the references were to pull requests and other
  khuedoan repos.

2. Changed some instances of `khuedoan.com` to `saliman.net`, but only the ones that referred to 
  apps that would run on the cluster.  References to external documentation needed to stay the same.

3. Replaced `Asia/Ho_Chi_Minh` with `America/Denver`

4. Replaced `id_ed25519` with `id_rsa` and commented out the code in metal/Makefile that generates
  keys.  We can use our existing keys.

