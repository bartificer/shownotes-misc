# CCATP — Verification, Twitter, and Mastodon

With the mass migration from Twitter to Mastodon, and the recent controversies around how Elon Musk is changing the meaning of the Twitter blue checkmark, now seems the perfect time to talk about the concept of verification in general, and how it applies to Mastodon.

## What does it Even Mean to be Verified?

When ever anything brands itself as verified, there are four questions you have to ask yourself:

1. What's the **claim** being made?
2. What **evidence** is being offered to support the claim?
3. What **checks** are performed to compare the evidence to the claim, and by who? (Think people, organisations, and/or software.)
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

OV certs on the other hand require human checks. Your organisation needs to be registered as a business, charity, or formal government department/agency/office, and you need to actually answer the phone at a number that can be verifiably tied to the organisation through a recognised trusted mechanism. I have to go though OV once a year every year, and it's a giant pain! It takes both my time and the certificate authority's time, so, OV certs are not free.

Also, you can choose to go through an extra strict validation process, and then your OV cert gets upgraded to *extended validation*, or EV, which add more confidence in the validation, but doesn't change the claims.

OK, so we know what's being claimed, and the evidence that has to be presented to back up those claims, who does the checks, and how?

As already implied, *Certificate Authorities* do the checking. For DCV certs they run software to do the work, either software they wrote themselves, or open source software, and regardless of the software, they're probably using the open ACME standard.

How do you get to be a CA? Well, you need to be trusted by the browser makers, so, they have built a whole process around that. There's a trade body that meets regularly to set rules for CAs to follow, and the CAs are all regularly audited against those rules.

Notice how complex all this is getting! There are organisations, there are rules, there are formal procedures, there are audits, there are protocols, and there is software, and there are organisations full of people doing lots of things to make it all go. Trust worthy verification systems are complex!

But wait, there's more! We haven't gotten to the sharing part yet! How can a website securely and trustworthily share the fact that their server has been verified? Cryptography! The HTTPS cert itself is digitally signed by a CA to attest to the fact that they have received and proof for and checked all the claims encoded in the certificate. The browser maker has added the CA's *root certificate* into their software, so the CA's signature can be cryptographically verified, giving you confidence that the claims the cert asserts are true!

All that just to prove the address bar is not lying to you? Yup!

## Twitter Account Verification

Let's start in the pre-Elon world, what did the blue check on Twitter mean before Elon Musk took over the company and re-wrote all the rules?

LEFT OFF HERE!!!

## Mastodon Link Verification

TO DO