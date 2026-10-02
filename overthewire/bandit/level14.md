# Level 13 -> Level 14

The goal of this level is to find the password stored in `/etc/bandit_pass/bandit14`, which can only be read by the user `bandit14`. Rather than the usual scrambled password, we will get a private SSH key that can be used to log into the next level.

The commands I needed to use for this level were `ssh`, `scp`, and `chmod` which will be explained more in-depth later.

To begin with, when we use `ls` in the `home` directory, we see:

`HINT   sshkey.private`

The `sshkey.private` is already given to us and ready to use BUT we can't use `ssh` to `bandit14` while already connected to `bandit13`. For this reason, we are given the `scp` command which is used to copy files from other servers and place them in your own.

Now that we know the directory to access the `sshkey.private` file, we can apply the command:

`scp -P 2220 bandit13@bandit.labs.overthewire.org:/home/bandit13/sshkey.private .`

The `:` allows us to point to the directory needed with the `.` telling the server to put the file in the directory we are in, though we can replace it with something like `/home/user/Downloads` if needed.

Now that we have our private key, we must secure it so that no one else can read it besides admins or else we will get the error message:

`@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0640 for 'sshkey.private' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "sshkey.private": bad permissions`

We can secure it by using `chmod`:

`chmod 600 sshkey.private`

The `6` in the 3 digits gives read and write properties to admins while the two `0`s give no permissions to groups and everyone else.

Now we can use the command:

`ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org`

Which uses the `-i` parameter to indicate to use the files as the sshkey, allowing us to log into level 15.
