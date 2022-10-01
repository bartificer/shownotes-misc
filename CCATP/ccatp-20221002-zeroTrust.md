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

The first stirrings of what would become Zero Trust were at a CISO forum meeting in XXX in 2003, when the idea was referred to as *de-perimiterisation*.

The idea went through a few iterations over the coming years with significant contributions from major firms like Forrester Research, Gartner, and Google (who named their series of whitepapers on the topic *BeyondCorp*). The idea really took off when NIST formalised their version of the concept in 2020.

Today, all the major vendors are advising their customers to adopt Zero Trust, and many are providing detailed guidance on how to migrate existing systems to Zero Trust. Two years ago only one in five *'cybersecurity decision makers'* were familiar with the concept, but a study by Okta this summer found near-universal adoption with just about every organisation surveyed either planning a transition or in the process of one.

## Just Three Principles! (and some pillars)

Despite being quite a loose term expressed in many different ways, Zero Trust always boils down to just three principles:

1. *'Never Trust, Always Verify'* — continuously verify all identities, not just users, but also devices & apps.
2. *'Just-enough just-in-time Access'* — give users the access they need, when they need it — no more than they, and no longer than they need it.
3. *'Assume Everything can be Hacked'* (sometimes stated more strongly as "Assume Everything **is** Hacked") — detect problems quickly, and *'limit the blast radius'* with *micro-segementation* .

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

## Limiting Privileges

## Assume Breach

## Links
* NIST's [Zero Trust Architecture](https://www.nist.gov/publications/zero-trust-architecture)
* Zero Recent Trust Status Reports:
	* Summer 2021 — [Microsoft](https://www.microsoft.com/security/blog/2021/07/28/zero-trust-adoption-report-how-does-your-organization-compare/)
	* Summer 2022 — [Okta](https://www.okta.com/resources/whitepaper-the-state-of-zero-trust-security-2022/thankyou/)
