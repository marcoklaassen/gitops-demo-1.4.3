# SOPS PGP

## Prerequisites

* gpg installed
* sops installed
* Editor configured (i use atom and added `export EDITOR="atom -w"` to my `.zshrc`)

## Demo usage

* Generate Key with `gpg --full-generate-key`
* set Fingerprint with `export SOPS_PGP_FP="<your public key fingerprint>"`
* create secret with `sops foo-secret-sops.yaml` (opens your editor for editing)
* Save and close file and get the encrypted file
