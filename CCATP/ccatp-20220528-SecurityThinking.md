# CCATP 28 May 2022 — Thinking About Security

As a general rule, the more specific security advice is, the less useful it is, because it will have a short shelf life and apply only to specific scenarios. The most honest answer to a general security question usually stars with *'it depends …'* 🙂

So, rather than list out some soon-to-be-stale advice that probably doesn't apply to your precise situation, I thought it might be fun to share some of the ways I think about security. The digital world changes quickly, so you're always having to think about new things and rethink things you thought you were done thinking about. There are a million right ways to go make these kinds of judgements, but here are some of the things I keep in mind when I'm doing it.

## Keep Your Eyes and Ears Open, and React!

Don't wait on security news to come to you, keep yourself in the loop! If you're responsible for any computer systems, even just family stuff, you need to subscribe to at least one trustworthy security news feed of some kind.

If you wait to find out about problems until they make the evening news, you'll soon find out that's often too little too late as you survey the ruins of your digital life!

### Don't fall for 'Politician's Logic'

When something happens, take the time to think — don't rush in thoughtlessly!

There's a fabulous line in the classic British comedy series [Yes Minister](https://en.wikipedia.org/wiki/Yes_Minister) where Sir Humphrey describes what his colleague Sir Arnold calls *Politician's Logic*:

> "Something must be done, this is something, therefore we must do it!".
>  [www.youtube.com/…](https://www.youtube.com/watch?v=vidzkYnaf6Y)

To borrow an old cliché, when you have a shiny new hammer, the whole world will look like nails, but that's an illusion! Use the right tool for the job, not the one you most recently spend the most money on, or watched the most YouTube videos about!

### Don't Forget the Risk of NOT Acting!

The clip from Yes Minister above ends with the clichéd civil service fetish for the status quo:

> "… doing anything is worse than doing nothing"

**Wrong!** It's not for nothing that Sir Humphrey is an anti-hero — we grudgingly like him **despite** his obstructionism, not because of it!

Sir Humphrey knows that everything you choose to do comes with some risk, but he's forgetting that **there's a risk to doing nothing**! The choice isn't between multiple more or less risky actions, and the zero-risk status quo, but between risky actions **and** risky inaction!

Whether you're trying to make your own informed decision, or making a recommendation to a manager or change-control-board, **train yourself to always consider the risk of inaction!** There may be aspects of life where the risk from doing nothing really is zero, but security rarely falls into that category!

### Remember that Risks Grow!

On a very related note, when you run into the inevitable difficult choice, **always err on the side of stronger protections**!

Why? Because the bad guys forget nothing, and are always learning. The amount of harm attackers can inflict on the first day a vulnerability is discovered is nothing more than a baseline — the absolute best you can hope for is that no one finds any way to make better use of the issue ever, and that's not even vaguely realistic!

I always think of Bruce Schneier's pithy line (from [Schneier on Security](https://www.schneier.com/)):

> "Attacks always get better."

In my mind I used to think of that as *Schneier's Law*, but I've had to update my naming scheme because it turns out he already has an older law, so I suggest we all start calling this *Schneier's Second Law*!

In case you're wondering, Schneier's first law is the perfect argument against rolling your own encryption or other security algorithm:

> "Any person can invent a security system so clever that she or he can't think of how to break it."

So, **always over defend**, and if the decision is **borderline, err on the side of taking action**. The chances are high that the problem is about to get worse than you think!

## React Fast, but also Preempt!

So far I've focused mostly on making decisions when something happens, in other words, reacting to some kind of change. Maybe it's the release of a new attack tool, the discovery of a vulnerability, the rise of a new attack technique, or maybe it's a change of circumstance. Maybe say everyone's just been forced to work from home with no notice 😉. It could also be the rolling out of a new system or service that will make people's lives better in some way, but also opens up new attack surfaces.

It's annoying, but in security, even the best prepared people will be forced to react to events on a regular basis. But the more prepared you are, the less often you'll need to react, and the less you'll need to do in haste. If you keep everything patched, and news comes out of a nasty exploit in active use that was patched last month, no problem! You do a quick check of your audit logs, verify the patch did get applied, and move on with your day!

### The Inverted Pyramid of Pain

OK, so I've convinced you to be proactive — now what? There are literally infinitely many things you could do. Where do you start?

You might fear that the stuff that's easy to do won't give you much of an impact, but thankfully, you'd be wrong!

Attacks follow a so-called *power law*. This means simple attacks are very frequent, while complex attacks that involve as-yet-undiscovered zero-days are very rare. Defending against the un-known un-known is really hard, but defending against the simple stuff is actually quite easy!

This is often shown in slide-decks as an upside-down triangle with easy to do things high on the chart, and the width of the triangle representing the effectiveness of the actions.

I don't find it intuitive to graph based on easiness rather than difficulty, but it's a cool and catchy name, so I'm fine with it 🙂

Anyway, the bottom line is wonderful — **do the easy stuff first** because it will give you the best results for your efforts!

So what kind of easy stuff can you do? The most powerful thing is to cover your proverbial rear, or, in fancy language …

### Minimise your Attack Surface

The fewer things there are for an attacker to attack, the fewer attacks you're likely to suffer!

- If you don't need an app, don't install it. If you stop using stuff, remove it
- If you test 5 things, delete the four you don't pick
- If you don't host any servers from your network, make sure your router blocks all in-bound connections. 
- If your server is only serving web pages, block all but the web ports. 
- If you have a web application delivery controller, block direct access to the back-end web servers and only open it to the ADC. 
- If your mail server is off-premise, block outbound SMTP traffic. 
- If you have multiple logical groups of things, group them into separate networks with firewalls between them. 
- If you router has WiFi but you don't use it, turn it off

**Don't stop yourself or your family/co-workers doing the things they need to do, but don't leave things on, installed, or open needlessly!**

### The Principle of Least Privileges

The privileges users, apps, and devices have on your systems are a very important part of your broader attack surface. And that's where the *principle of least privileges* comes in. There's no single official wording, but it goes something like:

> "Everyone  and every thing should have all the privileges needed, but no more."

That's an impossible target, a bit like *inbox zero*, but it's a fantastic thing to strive towards. Sure, practicalities will stop you from locking things down completely, but every little bit of granularity you add helps keep you safer.

## Think Defensively

Something I'm very passionate about is what I call a defensive mindset. Think of it as the security equivalent of defensive driving. You try to anticipate likely mistakes and problems, and try to deploy some mitigations upfront.

In Ireland, to drive a firetruck, you need to pass a defensive driving course. I've had a friend explain it to me, and it stuck with me. It teaches drivers to assume their fellow road users will do the dumbest things, and be ready to react when they do. If there's a car making a turn across your lane (a right turn here in Ireland), and you're not sure they've seen you, assume they've not seen you. If a ball rolls out into traffic, assume a kid is about to follow and slow down. Be sure you have the equipment you need should you get caught out in extreme weather, and so on.

Translating that way of thinking to the world of computers, I arrive at two concrete pieces of advice:

1. Think of likely problems, and do what you can to minimise their effect before they happen
2. Seek out assumptions, and replace them with controls

For example, if you think it seems likely your users will install unauthorised apps, put some logging and alerting in place so you get notified, and have your *spiel* on the dangers of "Shadow IT" prepared.

If you're assuming that the only IPs that will be accessing your domain controllers are from the IT department's subnet, deploy a firewall to enforce that assumption.

## Spread the Word!

No matter how hard you work to keep your family or your colleagues safe, nothing you do can protect them from their own naiveté. If we really want to protect people, we have to help them hone their IT "spidey sense" enough to stop and pause when something's not quite right. They don't need to know what to do, they just need to be vigilent enough to stop and ask for a second opinion!

Like it or not, **we all need to be evangelists**.

### Don't Moralise!

I chose the word *evangelist* carefully — think Guy Kawasaki evangelising the Mac with a giant big smile on his face and a real willingness to listen and offer constructive suggestions. Meet people where they are, and help them move themselves in the right direction.

The single best way to ensure your advice gets ignored is to moralise at people — if you try to shame or guilt people into doing the right thing you're almost certain to fail, and everyone just ends up cranky at everyone else!

### 'See something, say something!'

Finally, try to recruit your family and friends into the security fight by encouraging them to say something when they see something odd. Would you rather have 100 false positives or one false negative? In security, you want the former, not the latter. You might get 100 people telling you something odd happened but it's nothing to worry about. But the 101st person might tells you something that lets you see a ransomware gang's first toehold before they can establish a foothold and unleash hell. hTat's a massive win compared to the world where everyone's afraid if being wrong so you hear nothing until it's too late.

## Stay Curious!

At the end of the day, the single most important thing you can do to protect your security is stay curious. Learn about new tools, read reports on new attacks, take on board the advice from others, and just keep soaking it all up. **You'll never know everything, but you can always learn more!**