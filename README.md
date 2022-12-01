# What Are Passkeys and Why Should I Care?

You may have heard of the new passkey standard being touted by big players in the tech space like Apple, Google, and Microsoft as "the revolutionary new passwordless authentication method". However, that's probably all you know, if even that. So what is a passkey? And what does that mean for user authentication and the security landscape as a whole?

## Understanding Passwords

In order to understand passkeys, we first need the context of biggest player in the current security landscape: passwords.

You are likely pretty familiar with what a password is by now and maybe even how it works. At it's core, a password is a string of characters that a user provides to a website or service in order to prove that they are who they say they are. Passwords are to be kept secret in order to prevent others from logging into your account without your permissions. Additionally, they are almost always used in conjunction with some form of ID; a username, email, or phone number to name some options.

This method of authentication is extremely commonplace and easy to use for the masses. Plus, it has the added benefits of being easy to share with others (just send them your password!), as well as easy to reset in the event of a forgotten password.

However, there are numerous downsides to passwords to be aware of and to be solved.

### The Dark Side of Passwords

As the FIDO Alliance (one of the primary organizations behind the passkey standard) [desperately wants you to know](https://fidoalliance.org/passkeys/), passwords are easily phished. Creating a fake website such as https://goog1e.com is incredibly easy and effective at tricking victims into entering their passwords into an attacker's website. It can be challenging - especially for the less tech-literate among us - to distinguish a real website or URL from a fake. It's a huge problem!



Ideally, the server would never receive the user's password, but instead a hash of the user's password. A hash is a one-way (irreversible) operation performed on a string of characters, changing it to a seemingly random, but entirely unique, different string of characters.