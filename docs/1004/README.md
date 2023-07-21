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

### Get and copy the public key

`cat ~/.ssh/id_rsa.pub`

### Navigate to your Github personal account page and Generate a new SSH key

1. Paste your copied SSH key located in your personal account settings, listed under Access - SSH and GPG Keys section.

### Now we need our commits to be signed with a GPG key. (This proves they came from a trusted source).

1. Generate a new GPG Key

`gpg --full-generate-key`

1. Leave the default type selected and make the key at least 4096 bits long.

1. Enter your info and the email of your github account.

??? tip " To generate a Stronger key"
    We need to generate a lot of random bytes. It is a good idea to perfom some other action (type on the keyboard, move the mouse, utilize the disks) during the prime generation; this gives the random number generator a better chance to gain enough entropy.

### Now we will list the Private key pairs

`gpg --list-secret-keys --keyid-format=long`

### Then export the GPG public key by using the key ID listed in the first column named sec.
`sec  rsa4096**************** 2022-10-12 [SC]`

1. Copy and paste the key listed after the rsa4096 (`****************`)
1. Now copy the entire key over to your Github website under the **'Create a New GPG Key'** Section.

### Now make sure you are in the repo folder!

1. Get the ID by listing the key pairs and copying the portion

`gpg --list-secret-keys --keyid-format=long`

 1. Enable commit signing locally

 `git config --local commit.gpgsign true`

 1. Specify the ID of the key will be used

 `git config --local user.signingkey ****************`

### We will now test the config by commiting something.

