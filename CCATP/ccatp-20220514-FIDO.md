# CCATP — Why FIDO Passkeys Rock (14 May 2022)

This week the FIDO Alliance announced that they had partnered with Apple, Google & Microsoft as well as the W3C to develop a new standard to allow secure and convenient password-less authentication on the web and in apps. The project is driven by two complimentary aims — to remove the pain-points that are preventing the current FIDO2 and WebAuthn standards from gaining main-stream adoption, and to make phishing much more difficult.

It's important to note that what was announced was not a finished product, but an agreed specification and a commitment from the three major OS vendors to implement it this year. A lot of the practical details remain to be worked out, but there's a lot to be learned from we do know already, and it paints a picture rosy picture!

## How we got to Now

To understand the pain-points being addressed, we need to take a step back to look at FIDO's evolution over time, and why it's growth has been steady, but not exponential.

Before the FIDO Alliance there were proprietary hardware tokens and dongles of various kinds, and they either required the human to transcribe things, pretended to be a regular input device like a keyboard, or required custom drivers. These early dongles were only adopted by people and organisations with a lot to lose who were well motivated to put up with the expense and the hassle. Regular folks generally only saw these kinds of dongles in use in large corporations and government agencies, usually to control VPN access, and in financial institutions to protect the flow of money. Even PayPal got on board with the so-called *PalPal football*!

Most regular people moved to SMS-based 2FA, and later GoogleAuth-style authenticator apps, but the need for hardware tokens remained for those with the biggest security needs. The first FIDO standards were developed to standardise the interface between hardware tokens and computers and apps.

FIDO2 was the next bite at the Apple, and it built on the original FIDO spec by defining a new spec that would allow a smartphone to act as a hardware toke, and to allow browsers and websites to make direct use of the hardware tokens via the WebAuthn API. In the FIDO2 world it was like everyone's smartphone had a built-in hardware security token, and that token could be used to authenticate against the OSes, apps, and websites.

FIDO2 has definitely increased the use of FIDO, with major cloud services providers like Microsoft encouraging users to enable phone-based logins on their accounts. Places that require extra security like financial institutions are also on board, as are important digital infrastructure sites like GitHub.

Personally I'm using FIDO2, or FIDO2-like systems (vendors often don't call out their low-level technologies), to authenticate against Azure AD (to access Office365 and much more), GitHub, Adobe Creative Cloud, and my bank.

## What are These Pain Points?

Remember that with FIDO2 your phone becomes your hardware token, think if it like supergluing a YibuKi to the back of your phone!

If you only ever used your phone to log in to things then it could authenticate you directly if the app or website you were using supported FIDO2/WebAuthn, but in reality, that's not how we use the kinds of services we need to log in to. We don't just want our email on our phones, we want it everywhere!

So how do the vendors get around this? They make you install and *Authenticator* app that acts as a bridge from your phone to their servers.
When you try to log in, the server sees you have a FIDO token so it sends a push notification to their app on your phone asking you to authenticate via their app. The app is on your phone, so it can use FIDO to check you really are you, and the app then replies to the server to let it know whether or not to let you in.

This is clunky, but it gets worse!

If you have multiple phones you need to enrol each separately into all your services. A chore to say the least, but one most people can avoid.

But it gets much much worse, when you replace your phone, you have effectively thrown away your hardware token, your new phone is also a brand new hardware token! So, each time you get the latest shinny new hotness from Apple or Samsung or who ever, you have to re-enrol all your accounts. That's such a pain that two of the file Office365 accounts I have tokens for in my phone still have red exclamation marks telling me I need to re-enrol 8 month after I got my iPhone 14 Pro!

## So What's Changing?

What the FIDO Alliance announced this week is a move away from devices as hardware tokens, to authentication with public-private key-pairs being referred to as *passkeys*. These passkeys will be managed by the OS, and the OS may back them up and synchronise them between devices. The OSes will be responsible for protecting the passkeys, and that could be done with biometrics. To allow logins from 3rd-party devices, bluetooth can be used to authenticate from a near-by device that has the needed passkey.

From the user's POV they would enable a passkey on a site or in an app once, and then be able to use it directly, without the need for a helper app, from any of their devices. When they sign in to a new device their passkeys would sync down to them, and they'd continue to log in securely without having to re-enrol anything.

On devices they don't own there would be OS-level support for authenticating to sites and apps via a bluetooth connection to a nearby device that has the needed passkey.

### What are *Passkeys*?

Passkeys are just asymmetric encryption keys, one denoted as being private and securely managed by the user's OS, the other being public and given to the website or app to be authenticated against. With asymmetric crypto anything encrypted with the public key can only be decrypted with the matching private key, so to check if someone has the private key you simple encrypt some gibberish, send it to the person trying to authenticate, and ask them to give it back to you un-encrypted, if they can, they have the private key, so let them in. Notice that the website is not storing anything secret — if there's a data breach it's only the **public** key that's exposed!

To prevent cross-site/app tracking each site/app will get their own passkey.

## How Does this Help Fight Phishing?

One of the points the FIDO Alliance's PR team have been keen to highlight is that passkeys are not phishable — the site you're authenticating to never requires you to send a permanent secret to it, so there's nothing of value for a phisher to try trick you into handing over. If a site manages to steal your public key, and if they manage to trick you into trying to authenticate, then what do they get? A copy of the gibberish they sent you, nothing more!

But the protection is even better, because unlike a human, computers are not fooled by subtle typos or confusing special characters, so the passkey won't even be presented for you to try use if you're not where you think you are!

## Is This Better than Passwords with a Password Manager?

From a user-experience POV there won't be much difference — they're computer will offer them the appropriate credentials at the appropriate time, and the credentials won't be offered when on a fake site. But the fundamental flaw in the whole password concept **is** addressed by passkeys — **you don't have to entrust secrets with third parties**. 

Passwords are **shared secrets**, so every time you sign up to a password-protected site or service you are entrusting a valuable secret with them. Anyone who gets hold of that secret can assume your identity on that site or service. It certainly is possible for trustworthy sites and services to securely store passwords by using appropriately strong algorithms with a sufficiently high source of randomness to salt and hash the passwords. But, you are the end user have no way of know if that's actually happening — you **must trust**, and **can't verify**!

At this stage it's pretty darn clear that we simply can't trust sites or services to protect our passwords, literally billions of them have leaked in recent years!

**With passkeys you don't need to entrust any secrets** to the sites or services, **so there're nothing to protect**, and nothing to verify!

## Open Questions

This all sounds very promising, but the actual user experience will be up to the OS vendors to provide, and it remains to be seen how they'll do.

For this to stand a chance we'll need the syncing of the private keys to be both reliable and secure. All the major vendors have experience syncing secrets between devices, so a good experience **within a single ecosystems** seems very likely. What's a lot less clear is what the experience will be for switchers and sliders, i.e. those moving between ecosystems, or even simultaneously using multiple ecosystems at once.

In terms of authenticating to apps the OS vendors can do all the work, but what about the web? All the major OS vendors provide 1st-party browsers, so I'm sure they'll be well supported, but how will the OS interact with 3rd-party browsers? The fact that that kind of interaction already exists for WebAuthn gives me hope this will work out just fine, but that does leave me with one very big question.

What about the websites and services? All the sites and services that currently use passwords (hopefully with multi-factor authentication) are architected to store passwords (hopefully securely), with passkeys they'll need to store public keys instead. Will that prove to be a problem?

Probably not for any sites and services that already offer 'log in with X' buttons. Those buttons are sign-on mechanisms, so they sites are already storing SSO tokens rather than passwords for the users who choose to go that route. Even better, most sites that offer multiple sign-on options make use of commercial or open source libraries to provide the desired array of options, so updating a few popular libraries will make passkeys pretty ubiquitous pretty quickly.

There are also practical questions like how Apple, Microsoft, and Google will secure the syncing of your passkeys, ironically, they may be forced to continue to require passwords, at least as an optional fall-back for single-device users. If you have multiple devices you can use a second device to authenticate to the first, but what if you only have one device and you lose it and need to restore your passkeys to its replacement? Until you prove your identity to the guardian of your keypasses, you can't get the keypass you need to prove your identity! It's a classic circular dependency 🙁

## Next Steps

Over the coming months Apple, Google, and Microsoft will get busy adding OS-level support for passkeys to all their devices.

Presumably in parallel with that, APIs for use by website and app operators   will be finalised and published, and sample implementations will be released. We'd then hope to see major authentication libraries adopt support, and the relevant sites and apps begin to enable the protocol, or at least start planning for enabling it at or shortly after launch.

I'll be paying particular attention to three things:

1. How the OS-vendors implement the creation and syncing of passkeys
2. How the OS-vendors provide interoperability for at least switchers, and hopefully sliders too
3. How third party browsers incorporate the new APIs
4. How quickly websites and apps roll out support

## Further Reading
 
 * The official press release from the FIDO Alliance: [fidoalliance.org/…](https://fidoalliance.org/apple-google-and-microsoft-commit-to-expanded-support-for-fido-standard-to-accelerate-availability-of-passwordless-sign-ins/)
 * [Apple, Google, and Microsoft want to kill the password with “Passkey” standard — arstechnica.com](https://arstechnica.com/?p=1852374)
 * An interview with the FIDO Alliance's head of PR: 🎧 [Checklist 278: Getting to Know FIDO — overcast.fm/…](https://overcast.fm/+HLr56BDrs)
