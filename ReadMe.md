# Working with multiple git accounts

There might be cases where you have multiple git accounts  one on GitHub, another one on Bit-bucket or multiple accounts with the same provider like Bit-bucket. 

### 1. Create a new SSH Key

*ssh-keygen -t rsa -b 4096 -C "email@example.com"*

Save the key files as id_rsa_[name], e.g. id_rsa_gitgmailpersonal. This generates a public/private key pair in the chosen directory, usually C:\Users\[user]\.ssh\.

### 2. Save the ssh public key in the git remote account by copying and pasting the .pub file under the SSH public keys section after giving it a name. 

###3. Next, because we saved our key with a unique name, we need to tell SSH about it. Within the Terminal, type: ssh-add ~/.ssh/id_rsa_[name]. If successful, you'll see a response of "Identity Added." If ssh-add complains - Could not open a connection to your authentication agent, then execute this - eval "$(ssh-agent)" to explicitly invoke the ssh agent and try again.

### 4. Create/modify the git config file

If the .config folder doesn’t exist in the C:\Users\[user]\.ssh\ folder, create one using touch config command.Open the file and paste the following:

*#Personal GitHub*

*Host [uniquename] # e.g. git-gmailpersonal*

  *HostName [real hostname] # e.g. github.com*

  *IdentityFile [path to the ssh private key just created] # e.g. ~/.ssh/id_rsa_gitgmailpersonal*

### 5. Test it out

Create a new test folder named test. On the git terminal type the following commands to add a commit to the local repo:

*git init*

*touch readme.txt*

*git add .*

*git commit -m “First commit”*

Login into the git provider to create a new repository named test and push the local repo to the remote repository.

*git remote add origin git@alias:<accountname>/<reponame>.git*

Replace alias with the unique host name provided in the config file earlier. Account name is the remote repository account name. Reponame is the new repository name just created remotely.

E.g. git remote add origin git@git-gmailpersonal:virtualam/test.git

*git push -u origin master*








