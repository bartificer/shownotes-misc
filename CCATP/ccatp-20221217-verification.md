# CCATP — Verification, Twitter, and Mastodon

With the mass migration from Twitter to Mastodon, and the recent controversies around how Elon Musk is changing the meaning of the Twitter blue checkmark, now seems the perfect time to talk about the concept of verification in general, and how it applies to Mastodon.

## What does it Even Mean to be Verified?

When ever anything brands itself as verified, there are four questions you have to ask yourself:

1. What's the **claim** being made?
2. What **evidence** is being offered to support the claim?
3. What **checks** are performed to compare the evidence to the claim, and by whom? (Think people, organisations, and/or software.)
4. What's the process for  **sharing** the result of the verification?

That might sound simple, but there's actually a lot to think about!

Firstly, any validation system that's actually useful has to be very clear about exactly what's being verified. You may find that when you look more closely the claim is very limited, or worse, doesn't actually imply what you thought it did. The classic example is the padlock on a website — some people think that means the website is *'safe'*, but but that's not the claim HTTPS verifies! (More on that later.)

Secondly, what evidence does the claimant have to provide to back up their claim? Verification has to be supported by evidence, or its not verification, and the strength of that evidence is fundamental to the level of trust you can have in the validation. To get a basic HTTPS cert you simply need to prove you control the website by uploading a special file, setting a special DNS record, or replying to an email at a special address on the website's domain. 

Finally, there has to be a rigorous process for comparing the proof with the claim, and the result of that comparison has to be communicated in a credible, secure, trustable way.

Verification really is like a chain — the weakest piece dictates the overall strength. If the claim is meaningless it doesn't matter how well it's backed up, checked, or communicated! If the claim is meaningful, but the evidence is easy to fake, then it doesn't matter how rigorously the evidence was compared to the claim, or how securely it was communicated, it's trivial to fake! If the checks badly designed or poorly carried out, it doesn't matter how strong the claim is or how good the evidence being requested is, if the checks can't be trusted the outcome is worthless. Finally, if the claim is meaningful, the evidence strong, and the checking robust, it's all for nothing if the communication of the competed verification is ineffective, or worse yet, insecure. If real verifications are impossible to distinguish from fakes, it doesn't matter one jot how good the real verifications are!

## The HTTPS Example

We already know that the padlock in our browser isn't making the claim that the website is safe, so what claim is it making?

It's making at least one claim, but it could actually be making two claims. When you see that padlock in your browser's address bar the claim that's always being made is that you really communicating securely with the website the address bar says you're at. In other words, there has been no chicanery to trick your browser into connecting to the wrong IP address, no machine in the middle has altered the content en-route, and the transfers are encrypted. At a technological level that's actually a big claim, but notice there is no claim made about the quality of the actual content of the website, and there is no claim being made about the identity of the website's operator either! Yes, we have a secure communication channel, but all we know about the other end is that the URL we see is really the URL we're at. That tells us nothing about how safe the content is!

If the address bar is telling you you're at a URL that's like your bank's but not your bank's, then the padlock just means you're securely communicating with  a phishing site!

All HTTPS certs claim to verify one or more domain names, and verifying control over a domain name is easy to do and to check, so it's possible for these basic *Domain Control Validation* (DCV) certs to be free. But, if you choose to buy an HTTPS cert, you can add an additional claim — you can have the cert verify both domain names, and, an organisation. These *Organisation Validation* (OV) certs can tell you that you're really at your bank's domain, and, that your bank really does own that domain.

So what's the proof behind an HTTPS cert?

For a DCV cert you simply have to prove that you control the domain(s) you're getting a cert for. You can do that in three ways — you can upload a special file to the website, you can set a special DNS record on the domain, or you can answer an email at a special address at the website's domain (e.g. hostmaster@domain.tld).

Like I said, this is easy to do, and even easier to verify automatically, so DCV certs can be issued entirely automatically.

Organizational Validation certs on the other hand require human checks. Your organisation needs to be registered as a business, charity, or formal government department/agency/office, and you need to actually answer the phone at a number that can be verifiably tied to the organisation through a recognised trusted mechanism. I have to go though OV once a year every year, and it's a giant pain! It takes both my time and the certificate authority's time, so, OV certs are not free.

Also, you can choose to go through an extra strict validation process, and then your OV cert gets upgraded to *extended validation*, or EV, which add more confidence in the validation, but doesn't change the claims.

OK, so we know what's being claimed, and the evidence that has to be presented to back up those claims, who does the checks, and how?

As already implied, *Certificate Authorities* do the checking. For DCV certs they run software to do the work, either software they wrote themselves, or open source software, and regardless of the software, they're probably using the open ACME standard.

How do you get to be a CA? Well, you need to be trusted by the browser makers, so, they have built a whole process around that. There's a trade body that meets regularly to set rules for CAs to follow, and the CAs are all regularly audited against those rules.

Notice how complex all this is getting! There are organisations, there are rules, there are formal procedures, there are audits, there are protocols, and there is software, and there are organisations full of people doing lots of things to make it all go. Trustworthy verification systems are complex!

But wait, there's more! We haven't gotten to the sharing part yet! How can a website securely and trustworthily share the fact that their server has been verified? Cryptography! The HTTPS cert itself is digitally signed by a CA to attest to the fact that they have received and proof for and checked all the claims encoded in the certificate. The browser maker has added the CA's *root certificate* into their software, so the CA's signature can be cryptographically verified, giving you confidence that the claims the cert asserts are true!

All that just to prove the address bar is not lying to you? Yup!

## Twitter Account Verification

Let's start in the pre-Elon world, what did the blue check on Twitter mean before Elon Musk took over the company and re-wrote all the rules?

The blue tick's claim was very strong — "this account is the person/organisation it claims to be", but the evidence and checks were utterly opaque, basically boiling down to *"trust us, we did the work, and we did it well"*. Finally, the communication was simple, some account metadata that the website rendered with a blue icon.

Notice how trust was absolutely central to the whole thing? Many, me included, considered pre-Elon Twitter worthy of that trust, we we trusted the blue ticks. Now that Elon has taken over the claim is in flux, does it just mean the account paid, or does it mean some actual identity checks were done? Hard to tell really, and of course, the evidence and checks are still 100% *"trust us, we'll do it right"*. Personally, I have no trust in the current Twitter, and I don't think I'm alone in that!

## Mastodon Verification

Twitter's verification entirely depended on there being a central organisation to trust — Twitter, Inc. Mastodon is a federated system without an obvious central authority where Twitter-style verification could be done, so there is no exact analogue of Twitter's account verification on Mastodon. However, there are a number of different verified claims possible on the system.

### Mastodon Link Verification

There is one official verification option built into the Mastodon specification — Profile Link Validation. You can add up to four links to your Mastodon profile, and it is possible to have those links be marked as verified.

So what's the claim? The claim is that the person who controls the Mastodon site also controls the linked site(s). That's it! So the credibility of the identity entirely hangs in the credibility of the linked site(s). If someone has a verified link to their author page on a major news paper's website, that's a pretty strong indicator of identity, but a link to a random blog, not so much!

What evidence is required?

To verify your control of a linked site you must add a visible or invisible link from the site back to your profile that meets these simple criteria:

1. The URL in the profile must be secure, i.e. HTTPS
2. The linked page must contain either a visible link (`<a>` tag in the page's `<body>`), or an invisible link (`<link>` tag in the page's `<head>`) with a `href` attribute pointing to the Mastodon profile URL, and a relationship attribute (`rel`) which contains the value `me`, e.g. —

```html
<head>
  <link rel="me" href="https://mstdn.social/@bbusschots" />
</head>
<!-- or --!>
<body>
  <a rel="me" href="https://mstdn.social/@bbusschots">My Mastodon Profile</a>
</body>
```

I've done some testing, and redirects will be followed, so I have my links embedded in `https://www.bartbusschots.ie/s/`, but I have `https://www.bartb.ie/` redirecting there, and both links verify.

One annoying caveat is that it takes time for the validation to happen, so nothing happens immediately, so debugging this is a slooooow process 🙁

That covers the claim and the evidence, so how are the checking and communication done? Your Mastodon server does the check and then adds some metadata to your account. This is a very weak assertion, but that's OK because the check is so simple any Mastodon client can check for itself.

### Public Key Verification

If you use GPG public keys to communicate securely with people, you can add a verified link to your public key to your profile by using the free and open source [Keyoxide service](https://codeberg.org/keyoxide/).

The claim here is that the person who controls the Mastodon profile also controls the private key that matches the linked public key. This is useful for journalists who want sources to send them secure information.

### Implied Verification by Instance

Something which is emerging as Mastodon takes off is a kind of indirect implied verification through instance rules.

An instance has a domain name, and that domain name could be very credible. For example, the Whitehouse could run an official presidential Mastodon instance on the `whitehouse.gov` domain. That kind of thing is actually happening in Europe, with the European Parliament and German government running official instances.

The owners of these instances can set their own rules, and they can explicitly state them, saying for example that only government officials and elected representatives get accounts on the instance. This then becomes effectively like the old Twitter — if you trust the organisation that runs the instance to do what they say they do, then you trust the authenticity of all accounts on the instance.

## Final Thoughts

Powerful verification is **hard** — just look at how much work goes into that little padlock in your browser! No social network comes close to that, but if you trust the social network, they can offer believable verification, but you need to always understand what it is that is being verified. In the case of Mastodon the claim is that the link in the profile leads to a page owned by the profile's owner, and that page could also map that person to a PGP public key if they're one of the tiny minority of people who use that technology. Finally, in a federated system, the instance operator can also act as a source of verification — if you trust that the instance really is run by the organisation it claims to be run by, and if you trust that organisation to run the instance honestly, they you can trust the identity of the accounts on that instance.