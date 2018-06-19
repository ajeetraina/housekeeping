# How to Conduct Pull Request under GITHUB?


## Step-1: Open Git Bash.

Paste the text below, substituting in your GitHub email address.

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

This creates a new ssh key, using the provided email as a label.

## Generating public/private rsa key pair.


When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

```
Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter]

At the prompt, type a secure passphrase. For more information, see "Working with SSH key passphrases".

Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```

## Adding your SSH key to the ssh-agent

Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key.

If you have GitHub Desktop installed, you can use it to clone repositories and not deal with SSH keys. It also comes with the Git Bash tool, which is the preferred way of running git commands on Windows.

Ensure the ssh-agent is running:

If you are using the Git Shell that's installed with GitHub Desktop, the ssh-agent should be running.

If you are using another terminal prompt, such as Git for Windows, you can use the "Auto-launching the ssh-agent" instructions in "Working with SSH key passphrases", or start it manually:

```
# start the ssh-agent in the background
eval $(ssh-agent -s)
Agent pid 59566
```

Add your SSH private key to the ssh-agent. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_rsa in the command with the name of your private key file.

```
ssh-add ~/.ssh/id_rsa
```

## Add the SSH key to your GitHub account.

Go to github.com > Settings> and Add the id_rsa.pub key under /home/dell/.ssh/



```
[dell@wiki ~]$ git clone -b "master" git@github.com:ajeetraina/app.git somewhere
Cloning into 'somewhere'...
remote: Counting objects: 14096, done.
remote: Compressing objects: 100% (10/10), done.
remote: Total 14096 (delta 2), reused 3 (delta 0), pack-reused 14086
Receiving objects: 100% (14096/14096), 17.31 MiB | 686.00 KiB/s, done.
Resolving deltas: 100% (5116/5116), done.
[dell@wiki ~]$ cd somewhere/
[dell@wiki somewhere]$ git commit --amend -s --no-edit
[master c67ef11] Update README with the latest docker-app version
 Author: Ajeet Singh Raina, Docker Captain, {Code} Catalysts, Dell EMC R&D <ajeetraina@gmail.com>
 1 file changed, 1 insertion(+), 1 deletion(-)
[dell@wiki somewhere]$ git push -f
warning: push.default is unset; its implicit value is changing in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the current behavior after the default changes, use:

  git config --global push.default matching

To squelch this message and adopt the new behavior now, use:

```
git config --global push.default simple

```
See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)

Counting objects: 5, done.
Delta compression using up to 48 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 490 bytes | 0 bytes/s, done.
Total 3 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To git@github.com:ajeetraina/app.git
 + b58783d...c67ef11 master -> master (forced update)
[dell@wiki somewhere]$
```
