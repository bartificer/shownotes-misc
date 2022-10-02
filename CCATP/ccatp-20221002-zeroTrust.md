# Zero Trust Security

Cyberspace is a very dynamic place — the only thing that seems to be constant is change! This perpetual change means that things which were once best-practice from a cybersecurity POV soon become obsolete and ineffective, and new approaches are needed. That might sound like a very chaotic system, but there actually is some order in the chaos because the goals don't change. In NosillaCast jargon, *the problem to be solved* remains the same, like an ever present north-star.

## The CIA Triad

Regardless of how much the technology changes, the three competing coals for cyber security remain the same, and they go by the very impressive nickname of *the CIA Triad*:

1. **Confidentiality** — keep the secrets that need to be kept!
2. **Integrity** — prevent or at the very least detect unauthorised changes
3. **Availability** — users need to be able to access the services, apps, and data they need when they need them

Something to bear in mind is that these three things often conflict with each other, so cyber security is always a balancing act. An excellent way to ensure confidentiality and integrity is to turn the computer off, encase it in concrete, and burry it in an old disused mine, but that rather hinders availability 🙂

## The Old Model

In formal presentations you'll see the old way of thinking about cyber security described as *perimeter-based approaches*, but in less formal presentations you'll see it described using various analogies to medieval castles. There's the big bad world, the moat surrounding the whole castle, and the keep protecting the crown jewels.

So, you have an edge firewall controlling access to the LAN, the users in the LAN, and the servers in a nested data centre network behind another layer of protection.

How do you map this model onto our modern cloudy cyberverse? You can't!

## Zero Trust to the Rescue!

Before we dig into the details, it's very important to understand that Zero Trust is a loosely defined term, and you're best to think of it as a philosophy, framework, or strategy, and definitely don't think of it as a recipe or a checklist!

The other important thing to understand is that while it's popularity has exploded since the pandemic, it's not actually a new idea, it's just taken a while to mature.

The first stirrings of what would become Zero Trust were at a CISO forum meeting in Jericho in 2003, when the idea was referred to as *de-perimiterisation*.

The idea went through a few iterations over the coming years with significant contributions from major firms like Forrester Research, Gartner, and Google (who named their series of whitepapers on the topic *BeyondCorp*). The idea really took off when NIST formalised their version of the concept in 2020.

Today, all the major vendors are advising their customers to adopt Zero Trust, and many are providing detailed guidance on how to migrate existing systems to Zero Trust. Two years ago only one in five *'cybersecurity decision makers'* were familiar with the concept, but a study by Okta this summer found near-universal adoption with just about every organisation surveyed either planning a transition or in the process of one.

## Just Three Principles! (and some pillars)

Despite being quite a loose term expressed in many different ways, Zero Trust always boils down to just three principles:

1. *'Never Trust, Always Verify'* — continuously verify all identities, not just users, but also devices & apps.
2. *'Just-enough just-in-time Access'* — give users the access they need, when they need it — no more than they need, and no longer than they need it.
3. *'Assume Everything can be Hacked'* (sometimes stated more strongly as "Assume Everything **is** Hacked") — detect problems quickly, and *'limit the blast radius'* with *micro-segementation*.

You apply these principles across the equally loosely defined *pillars of IT*. Some descriptions use five pillars, but I'm most familiar with Microsoft's six pillars:

1. Users
2. Devices (*endpoints* in the jargon)
3. Apps & Services
4. Infrastructure (servers, firewalls, load balancers, etc.)
5. Networks
6. Data

## Start with Clear Policies!

When you try apply those three broad concepts across all those pillars you soon realise that Zero Trust is something the entire organisation has to buy into, it’s not something IT can do alone, let alone just the cybersecurity team!

Deploying apps and services, onboarding devices, managing users, and implementing security controls all involve making choices. Those choices should compliment each other and all pull in the same direction, and that’s impossible without high-level policies for guidance. The very highest levels of management need to be involved in writing **and maintaining** these policies, and everyone in the organisation needs to understand them.

### Segmentation

One of the most important decisions to be made is how to group and divide things, or to use the jargon — *segmentation*. For all your security controls across all the pillars to be effective they all need to be in alignment with each other, and the best way to achieve that is with a high-level policy that everyone is bought into. 

### Know Your Data

Another vital component of an effective high level policy is *data governance*. What do you have, where is it, how sensitive is it, how long does it need  be to be retained, who should and should not have access, from where, and who can it be shared with, and how.

This is probably the most difficult part of getting to an effective Zero Trust implementation!

## Some of the Cool Tech

Only when you know what you’re trying to achieve can you start to effectively deploy the fun tech stuff 🙂

A simple overview of just Microsoft’s offering is literally a 2 day course (I just took it and passed the exam 😀), so this can only be a little taster of what’s being deployed out there.

### Users & Permissions

In the old world you're logged in or you're not — it's a binary thing. With modern cloud services like Azure Active Directory (the identity brain of Office365) your login state is on a spectrum, and contains a lot of metadata. Your login has a risk score based on how confident the system is that you're really you, it has contextual information like where you are (IP and geographic) and what device you're using, and it captures the level of challenge you were presented with, i.e. did you pass just basic authentication, or did you pass Multi-Factor Authentication (MFA), and if you did, did you do it the old fashioned way with codes, or did you use a modern passwordless technology like Passkeys, the Microsoft Authenticator App, or Windows Hello?

Whether you're using a desktop app or a web app, each time you try to access a resource, your credential is passed to the back-end service, and it makes a fresh determination of whether or not to allow your request. You might be allowed to view your own documents from any device, but financial documents might only be allowed from corporately managed devices. Or, you might be allowed to use some apps without MFA, but be challenged for MFA when you move to something more sensitive. This all comes under the label of *conditional access*.

Access to shared resources should all be controlled at the group level, not the individual level. This is where the segmentation strategy comes in. Your position within the organisation will give you a defined set of group memberships, and its those groups that get granted rights to access resources. When you move department your groups get updated to reflect your new role (potentially automatically in really well architected systems), and the change will take effect instantly.

In more complicated apps and services where there are granular permissions those permissions should be grouped into sensible roles, and those roles should then be assigned to groups. This is known as *Role Based Access Control*, or RBAC.

All this is for regular user access, privileged access should be more tightly controlled, with some kind of *Privileged Access Management* or PIM. Ideally no user ever retains permanent privileged access, instead, users have the right to enable privileges when needed. For admins that's probably a self-service operation, but for technicians there can be approval loop in the processes. Either way, the privileged access will be for a limited time, and it will be audited.

You might wonder what the point of self-service PIM is, but it has two advantages over permanent privileges — firstly, there's an audit trail, but secondly, that ever-present authentication can step in and place restrictions on the escalation, maybe you can only assume your admin powers when on the corporate network, or when using a corporately managed device, or when on a specific VPN, or when not abroad, and so on. In other words, it provides a means for imposing a policy as an explicit security control instead of an assumed practice.

### Data

Once you've asserted control over who is doing what from where, the next step is to assert control over what they're doing things to, i.e., to govern your data!

All data in modern cloud systems has metadata effectively imbedded in it, so the information about the data travels with the data, and can't be easily separated from it. This metadata includes the usual stuff you might expect like timestamps and owners and contributors, but it also contains *data classification labels* and *data retention labels*. Classifications labels define what the data is, and retention labels enforce a life cycle on the data.

In terms of retention there are three kinds of data — data that can be kept as long as people want it, data that **must** be retained for a minimum length of time (e.g. financials), and data that **must not** be retained longer than a given period, probably due to some kind of data protection regulation.

When it comes to classification you're talking about labelling things like contracts as contracts, financial accounts and statements as financial data, and even tagging documents as containing specific pieces of sensitive information like credit card numbers. Some data classification is manual, some is rule based, but a lot is AI driven these days.

The key point is that once you data is labeled you can apply security controls to it on a file-by-file or record-by-record basis. 100 users might have access to the files area in a Team, but only those in the finance office would be able to view the SEC filings in that folder. You can also use the labels enforce *conditional access*, like some data only being available from corporately managed devices, or during work hours from the office etc..

Another important security control enabled by data classification is *Data Leak Protection* — this puts limits on how and by whom data can be shared.

Finally, data retention labels can be used to drive both automated backups, and, automated data retention rules, with the deletion of some files being blocked until the file is appropriately old, or automatically destroyed after a given amount of time.

### Devices & Apps

I won't dig deep into this area because it gets very deep very quickly, but an important point to note is that both devices an apps are authenticated with certificates of various forms. You can't limit what an app can do if you're not sure it really is that app you think it is!

One thing I do want to draw attention to is the evolution of device management (AKA MDM) — in the past it was also a binary thing, a device was either personal or corporate, but now it can exist on a spectrum, and different conditional access rules can be applied at different points on the spectrum.

At one end of the spectrum you have an unknown unmanaged device, then you have a registered but unmanaged device, and then you have the most interesting point on the spectrum, a partially-managed device, and finally you have fully managed devices. On a partially-managed device some apps and some parts of the file system are controlled by corporate IT, but the phone itself and all the regular apps and data are controlled by the user and not even accessible by corporate IT. The managed apps and data can be remote wiped without affecting the rest of the device.

### Infrastructure, Networks, Etc.

At this stage we're getting much too far into the weeds for this show, so I'll just say that the tools are evolving at an impressive rate, and end-goal these tools are empowering is *micro-segmentation*, that is to say, small islands of access that stop attackers in their tracks when the try to move from something they were able to hack to any other resource. In the industry jargon *'micro-segmentation blocks lateral movement in the post-exploitation phase'*. A much cooler way to say it is that it limits the blast radius of a hack!

## The Effect of Assuming a Breach

If you assume everything can be hacked, and at least something probably is at every moment, then you're very well motivated to install tools for finding and responding to security incidents. This is an area that's been growing very fast, and that I find really cool.

The first thing you need is a *single pane of glass* where all your logs come together. These kinds of systems are referred to as SIEMs (Security Incident and Event Monitoring). A good SIEM won't just aggregate your logs, but it will allow you to efficiently search the data, assemble it into custom dashboard and reports, and to configure various alerting rules when things happen.

A basic SIEM is great, but it will generate a lot of alerts, wouldn't it be good if you could automate your response? That's where the next acronym comes in — SOAR (Security Orchestration, Automation, and Response). When you add SOAR functionality to a basic SIEM you can automatically respond to security incidents without a human needed to be involved. You'd generally use SOAR rules to push systems into a safe state and raise the alarm. For example, if enough alerts are triggered to make it probable that an account has been compromised, disable it and let the service desk or security operations centre (SOC) know.

Automated alerts and responses can only get you so far. Your alert logic can't be perfect, especially in a rapidly changing world, and while in theory corporations should have dedicated security teams pro-actively hunting for problems, the reality is nowhere has enough staff to catch everything, and most places have no where near enough to catch even the low-hanging fruit! This is where AI comes in! A lot of modern attacks consist of stringing together steps that are not suspicious individually, but when you put them all together they are. AI can be trained to spot this kind of *'anomalous normal'* activity. Modern SIEMs that have this kind of functionality tend to be branded as XDR, for *eXtended Detection and Response*.

All of that means that a single pane of glass for security operations like Microsoft's Sentinel is now branded as SIEM/SOAR with XDR!

## Final Thoughts

Unless you're lucky enough to be starting from a scratch, the move to Zero Trust is going to be a gradual journey. It's going to take a long time, but a lot can be achieved quickly by starting with the basics and building it up from there. The universally agreed starting point is identity — the better a handle you get on authentication the more secure you can be. After identity comes asserting control over end-points and data, and then you're into icing the cake.

No more medieval castles — verify everything always, give as little access as is needed, and defend everything because there's no outer wall to protect you!

## Links
* NIST's [Zero Trust Architecture](https://www.nist.gov/publications/zero-trust-architecture)
* Zero Recent Trust Status Reports:
	* Summer 2021 — [Microsoft](https://www.microsoft.com/security/blog/2021/07/28/zero-trust-adoption-report-how-does-your-organization-compare/)
	* Summer 2022 — [Okta](https://www.okta.com/resources/whitepaper-the-state-of-zero-trust-security-2022/thankyou/)
* [Microsoft's Zero Trust Sales Pitch](https://www.microsoft.com/en-ie/security/business/zero-trust)
