# Level 6 -> Level 7 

The goal of this level is to find the password stored somewhere on the server which has the following properties:

- Owned by the user bandit7
- Owned by the group bandit6
- 33 bytes in size

The way I found this password was by using find:

`find -user bandit7 -group bandit6 -size 33c`

The only issue was that a lot of other directories and files fell under those circumstances. For this reason, I used `grep` to isolate/highliht the text needed:

`find -user bandit7 -group bandit6 -size 33c | grep password`

I then used cat to recieve the password.

Logged in as `bandit7`, found the password in the file `/var/lib/dpkg/info/bandit7.password`. Moving on to level 8.
