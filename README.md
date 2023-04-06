# git-secret-test

## workflow

### Setup encryption once for the repo

1. Setup repo
2. run `git-crypt init` -> creates `.git-crypt` folder in `.git`
3. add `.gitattributes` file and add files to be encrypted
4. now changes on encrypted files are encrypted automatically and transparent to the user
5. extract the key from the repo with `git-crypt export-key <keyfile>`
6. store the keyfile in a safe place and share it with collaborators

Adding collaborators to the repo can be done in two ways:

1. add collaborators to the repo with their own gpg key
2. share one key with all collaborators (poor practice but easier to manage and probably sufficient for small teams)

### Setup encryption for new checkout

1. clone repo
2. get the keyfile from the repo owner
3. run `git-crypt unlock <keyfile>` -> decrypts all files in the repo
4. From now on changes to encrypted files are encrypted automatically and transparent to the user

## Test decryption

For testing purposes the keyfile is stored in the repo (`./secret_key_for_test/exported_secret_key`). Of course you should never do this in a real project.


## Further reading

- [git-crypt](https://github.com/AGWA/git-crypt)
- <https://www.guyrking.com/2018/09/22/encrypt-files-with-git-crypt.html>
