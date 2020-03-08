Using bcrypt-sha256 to hash passwords. Bcrypt by itself is considered durable with the only limitation of truncating passwords if the password goes over a certain length. Running the password through the sha256 algorithm before using bcrypt mitigates this deficiency.

Credentials are stored in a plain text file in the format {user}:{hashed password}. In `secret.txt`, each user (`test`...`test4`) has a password of `P@ssword1!`. As you can see the hash is completely different from the next.

**Example Outputs:**

~User logging in successfully
```
Would you like to login [1] or register [2]? 1

Username: test
Password: 

[+] Welcome test!
```

~User logging in unsuccessfully
```
Would you like to login [1] or register [2]? 1

Username: test
Password: 
[-] Invalid Username or Password
Username: 
```

~User creating an account successfully
```
Would you like to login [1] or register [2]? 2

[!] Username Must Be Between 4-10 Characters and Must Not Already Exist
Username: test5

[!] Minimum Password Requirements: 8-20 Characters, One Uppercase, One Special Character, One Number
Password: 

[+] Account Created!
```

~User creating an account unsuccessfully
```
Would you like to login [1] or register [2]? 2

[!] Username Must Be Between 4-10 Characters and Must Not Already Exist
Username: test5
[-] Username Already Exists or Your Username Does Not Meet Length Requirements
Username: 
Username: test6

[!] Minimum Password Requirements: 8-20 Characters, One Uppercase, One Special Character, One Number
Password: 
[-] Password Does Not Meet Requirements
Password: 
```

~User exceeding login attempts then being forced to quit
```
Would you like to login [1] or register [2]? 1

Username: test
Password: 
[-] Invalid Username or Password
Username: test
Password: 
[-] Invalid Username or Password
Username: test
Password: 
[-] Invalid Username or Password
Username: test
Password: 
[-] Goodbye
```

**Installation:**

This was made with python 3.6.9 in Ubuntu 18.04 LTS

1) `cd` into a new directory and do `virtualenv env`
2) `source env/bin/activate`
3) `git clone https://github.com/n0pe13/kindof-Secure-Authentication.git`
4) `cd kindof-Secure-Authentication`
5) `pip install -r requirements.txt`
