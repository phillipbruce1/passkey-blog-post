# What Are Passkeys and Why Should I Care?

You may have heard of the new passkey standard being touted by big players in the tech space like Apple, Google, and Microsoft as "the revolutionary new passwordless authentication method". However, that's probably all you know, if even that. So what is a passkey? And what does that mean for user authentication and the security landscape as a whole?

## Understanding Passwords

In order to understand passkeys, we first need the context of biggest player in the current security landscape: passwords.

You are likely pretty familiar with what a password is by now and maybe even how it works. At it's core, a password is a string of characters that a user provides to a website or service in order to prove that they are who they say they are. Passwords are to be kept secret in order to prevent others from logging into your account without your permissions. Additionally, they are almost always used in conjunction with some form of ID; a username, email, or phone number to name some options.

This method of authentication is extremely commonplace and easy to use for the masses. Plus, it has the added benefits of being easy to share with others (just send them your password!), as well as easy to reset in the event of a forgotten password.

However, there are numerous downsides to passwords to be aware of and to be solved.

### The Dark Side of Passwords

As the FIDO Alliance (one of the primary organizations behind the passkey standard) [desperately wants you to know](https://fidoalliance.org/passkeys/), passwords are easily phished. Creating a fake website such as https://goog1e.com is incredibly easy and effective at tricking victims into entering their passwords into an attacker's website. It can be challenging - especially for the less tech-literate among us - to distinguish a real website or URL from a fake. It's a huge problem!

Another big problem is data breaches. Ideally, the server would never receive the user's actual password, but instead a salted hash of the user's password. A hash is a one-way (irreversible) operation performed on a string of characters, changing it to a seemingly random, but entirely unique, different string of characters. Additionally, salt is a randomly generated string of characters to be added to the user's password in order to prevent two users with the same password to have the same hash. This would mean that a breached password database is useless to an attacker. Not only are all of the passwords unrecognizable and irreversible, but due to the salt, even two hashes of the same password cannot be recognized as coming from the same source.

However, proper implementation of password storage and security is challenging and expensive. Even today, there are numerous websites and services which make the conscious decision to improperly store user passwords, leaving them vulnerable to breaches. This leads to another problem with passwords - password recycling.

In any other context, I would say recycling is great! However, when it comes to passwords, it is one of the worst, yet most common practices. According to a 2018 post from Panda Security, [52% of people reuse their passwords](https://www.pandasecurity.com/en/mediacenter/security/password-reuse/). Now, when one service gets breached, the attackers suddenly have access to every account that user recycled that password with. I've seen this occur firsthand several times.

### Solutions to Use With Passwords

There have been several solutions to these problems put forward and widely adopted already. There are two primary tools that are recommended though: multi-factor authentication (MFA) and password managers.

MFA (also commonly called 2FA) comes in many forms. In essence, MFA is the practice of using a second method of authentication in conjunction with a password. Options include sending a code via SMS or email, using a physical security key, Google's *press "yes" on your phone to sign in*, and using time-based one-time passwords (TOTP).  While these options do all increase the security of one's account, they all come at the cost of convenience. You are required to have your phone, smart watch, or other device on you or nearby in order to sign in. Additionally, it makes the whole sign in process take longer, which no one really *wants*.

The second option is to use a password manager. Password managers are exactly what they sound like: tools to help you manage your passwords. Popular providers like [Bitwarden](https://bitwarden.com), [1Password](https://1password.com), and even the password managers built into browsers like Firefox are highly trusted and respected in the security community. They undergo regular security audits, are built and maintained by security and encryption professionals, and operate under a strict zero-knowledge policy, meaning they encrypt your passwords in such a way that bars even them from being able to access your information.

Because a password manager stores your passwords for you, they have a feature which allows the generation and storage of random, unique passwords for each website or service. This solves the issue of reused passwords, as well as needing to remember dozens or hundreds of passwords. With a password manager, all the user needs to remember is their single master password. Additionally, password managers store the URL of the associated website. If a user tries to login to a phishing site, their password manager will not display the login information immediately because the URLs do not match. It's an excellent warning to potential victims.

However, even password managers still have their problems. There is an argument to be made against putting all of one's eggs in one basket. However unlikely or impossible, what happens if an individual's password manager gets hacked? Or their master password phished? Additionally, because most password managers use the master password to derive the encryption key for the password library, what happens when the user forgets their master password? The entire password library is lost, leaving the user to pick up the pieces and start over.

## What About Passkeys?

Enter [passkeys](https://fidoalliance.org/white-paper-multi-device-fido-credentials/). As mentioned previously, passkeys are being marketed as the passwordless way of the future, replacing passwords with biometric sign in methods. That sounds like it could be cool, although depending on how it's implemented, it could be a privacy and security nightmare. So, how does it work?

To put it simply, a passkey is actually a set of two keys: a public key and a private key. To the more tech-literate among you, this may be ringing a bell already: asymmetric/public key encryption. One key is generated randomly, then used to figure out the second key via a string of cryptographic equations. Once generated, the public key is sent to the website/server freely, while the private key is stored securely on the client's device.

> Something important to understand here is that the public and private key are derived in such a way that if one key is used as the encryption key, then other key is the decryption key. For example, if Alice wanted to send Bob a secret message, she could use Bob's public key to encrypt the message. Once encrypted, the only way to decrypt the message is with Bob's private key, which only Bob knows. Not only does it keep Alice's message secure and private, but it also ensures that Bob is the only one who can decrypt and read the message.

During the login process, the server sends a challenge to the client. This challenge is a pieced of data encrypted with the user's public key. The client must then complete the challenge by decrypting the data with the user's private key. If the client responds with the proper decrypted data, then the server knows that the user is who they say they are.

This system resolves numerous issues with passwords. First, because the user's private key is what's needed to login, password leaks/data breaches are a thing of the past. Servers and websites only have access to their users' public keys, which are useless on their own. It's impossible to store this information improperly, as it is of no worth to bad actors. Password recycling is impossible here as well. Because the key pair are randomly generated and extremely long and complicated, no two passkeys are the same and they are nearly impossible to guess. Additionally, similar to a password manager, passkeys are meant to autofill into the associated websites based on URL. If a user clicks on a phishing link, their passkey will not be able to autofill because the system recognizes that it is a different website.

In order to keep these passkeys organized and secure, providers have created systems that function a lot like a password manager. Let's look at [Apple](https://developer.apple.com/passkeys/) as an example. Apple's passkeys (the public/private key pair) are stored in their iCloud Keychain, right alongside a user's passwords. In order to decrypt a user's passkeys, they must provide some type of authentication, such as a pin, password, or biometric authentication via TouchID or FaceID. This makes the whole process very seamless for the end user: simply visit a website, select the passkey login option, authenticate via biometrics/pin, and the process is complete.

So, the standard is more secure and easy to use than a password and some of the biggest players in tech are in support of the standard? There must be a catch!

## Yes, There's a Catch

As a technology and a standard, passkeys definitely have a lot going for them. However, the current implementations available present numerous issues which, in my opinion, are deal breakers.

Starting off with the smallest issue: passkeys are hard to share. All of us have shared a password or two at one point or another, such as sharing a Netflix password to let a friend use your account ([R.I.P.](https://www.cnet.com/culture/entertainment/the-end-of-free-netflix-password-sharing-is-coming-heres-what-to-know/)). With passkeys, there does not seem to be any easy way to share - or even *view* - one's passkeys. Apple has a [support article](https://support.apple.com/guide/iphone/share-passkeys-passwords-securely-airdrop-iph0dd1796bb/ios) on the topic, but it relies on AirDrop, meaning both devices must be from Apple. On the other hand, Google doesn't even have a way to share a passkey with someone else. Pretty lackluster support if you ask me - especially for multi-trillion dollar companies.

This leads into the second issue: signing into accounts on a device you don't own. Let's say a user wants to sign into their email on a friends computer. With traditional passwords, they could just enter their password and be logged in. With passkeys though, the user requires access to a device they own and are already logged into. Google's solution is to [scan a QR code with your phone](https://developers.google.com/identity/passkeys/use-cases#sign-in-with-a-phone). From a convenience perspective, this can hardly be called a solution. Most people's major grievance with MFA is the need to keep their phone on them at all times and fiddle with it before signing in. Apple [follows suit](https://support.apple.com/guide/iphone/sign-in-with-passkeys-iphf538ea8d0/ios), requiring the use of a QR code.

The last issue with passkeys is the biggest *by far*: current implementations *do not allow users to export their passkeys*. This is a *huge* problem. For example, if an iOS user decides to switch to Android or vice versa, or a mobile user wants to get their passkeys onto their Windows computer, there is no possible way to export from one ecosystem to another. Instead, the solution from Google is [to add a new passkey to each separate website](https://developers.google.com/identity/passkeys/faq#can_i_move_synchronized_passkeys_from_one_platform_provider_to_another) for the new device. This is absolutely unacceptable. Setting aside the argument over the anti-consumer subtext of the situation, any good password manager has had this feature for *years*. Chrome, Firefox, Bitwarden, and 1Password all have the ability to export their password library to a file to be stored, encrypted, or imported into another password manager. It is a fact of life that people will change platforms, or use multiple platforms at once. What if a website does not support multiple passkeys? Or a user wants to get their dozens of passkeys from their iPhone in their Windows PC? As of right now, they would be expected to painstakingly add their PC to each individual website they are registered with. This is not a limitation of the technology or the specification either. It is simply the giant tech corporations refusing to add such a feature in order to lock their users into their own platforms. 

## So, Should I Use Passkeys?

Ignoring the fact that the vast majority of websites do not yet support passkeys and probably won't in the foreseeable future, should you start using passkeys with the websites that do?

It's up to personal preference. It is certainly a more secure protocol, so if that is your top concern, then it's not a bad idea to give it a go. However, for the average person - and even the techie ones among us - I would argue that it's better to sit this one out for now. The technology is cool and I have no doubt that we will start seeing this specification being supported on more and more websites. The issues I outlined above are holding it back way too much though. The lack of the ability to export my passkeys is already a deal breaker for me, while the need to keep my phone on hand and the challenge of sharing passkeys are just the cherries on top.

Personally, I will keep my eye on the technology and wait patiently for the issues to be fixed. I do believe that this is the way of the future and, at its core, a superior solution compared to conventional passwords. For now though, I'll stick with [Bitwarden](https://bitwarden.com) (shoutout :)) and conventional TOTP MFA. It's more than secure enough for all but the highest priority of targets and strikes a good balance between security and convenience for me.