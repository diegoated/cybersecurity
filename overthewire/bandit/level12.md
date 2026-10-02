# Level 11 -> Level 12

The goal of this level is to find the password in the file `data.txt`, where all lowercase and uppercase letter have been rotated by 13 positions.

To find the password we must familarize ourselves with Rot13. A letter substitution cipher that replaces a letter with the 13th letter after it in the Latin alphabet.

To begin deciphering, we must use the `tr` command and give it the sets it needs to decipher the text, being `A-Za-z` to `N-ZA-Mn-za-m`. We can implement this using the following command:

`tr 'A-Za-z' 'N-ZA-Mn-za-m' < data.txt` 

The output will be:

`The password is GROozWPO8QyN0mGrjUkID0WCYkZiQxrN`

Granting us access to level 13.
