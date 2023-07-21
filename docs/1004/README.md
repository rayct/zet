# Set up a GitHub repository with SSH and GPG on Linux

### Check Git Version
`git -- version`


### Set Global username/email config
`git config --global user.name "GITHUB_USERNAME"`

`git config --global user.email "EMAIL"`

### Generate new SSH Key

`ssh-keygen -t rsa -b 4096 -C "ADD_EMAIL_OF_GITHUB_ACCOUNT"`

1. Type a name for the key or leave the default one by pressing 'ENTER'
1. Enter a secure passphrase

### Initialze the SSH agent (Makes it easier to auth with SSH)

`eval "$(ssh-agent -s)"`

### Then add SSH key to list of keys maintained by the SSH agent

`ssh-add ~/.ssh/id_rsa`

1. Enter Password/Passphrase you created

