# CCATP 28 May 2022 — Thinking About Security

As a general rule, the more specific security advice is, the less useful it is, because it will have a short shelf-life and apply only to specific scenarios. The most honest answer to a general security question usually stars with *'it depends …'* 🙂

So, rather than list out some soon-to-be-stale advice that probably doesn't apply to your precise situation, I thought it might be fun to share some of the ways I think about security. The digital world changes fast, so you're always having to think about new things and re-think things you thought you were done thinking about. There are a million right ways to go make these kinds of judgements, but here are some of the things I keep in mind when I'm doing it.

## Keep Your Eyes and Ears Open, and React!

Don't wait on security news to come to you, keep yourself in the loop! If you're responsible for any computer systems, even just family stuff, you need to subscribe to at least one trustworthy security news feed of some kind.

If you wait to find out about problems until they make the evening news, you'll soon find out that's often too little too late as you survey the ruins of your digital life!

### Don't fall for 'Politicians Logic'

When something happens, take the time to think — don't rush in thoughtlessly!

There's a fabulous line in the classic British comedy series [Yes Minister](https://en.wikipedia.org/wiki/Yes_Minister) where Sir Humphrey describes what his colleague Sir Arnold calls *Politicians Logic*:

> "Something must be done, this is something, therefore we must do it!".
>  [www.youtube.com/…](https://www.youtube.com/watch?v=vidzkYnaf6Y)

To borrow an old cliché, when you have a shiny new hammer, the whole world will look like nails, but that's an illusion! Use the right tool for the job, not the one you most recently spend the most money on, or watched the most YouTube videos about!

### Don't Forget the Risk of NOT Acting!

The clip from Yes Minister above ends with the clichéd civil service fetish for the status quo:

> "… doing anything is worse than doing nothing"

**Wrong!** It's not for nothing that Sir Humphrey is an anti-hero — we grudgingly like him **despite** his obstructionism, not because of it!

Sir Humphrey knows that everything you choose to do comes with some risk, but he's forgetting that **there's a risk to doing nothing**! The choice isn't between multiple more or less risky actions, and the zero-risk status-quo, but between risky actions **and** risky inaction!

Whether you're trying to make your own informed decision, or making a recommendation to a manager or change-control-board, **train yourself to always consider the risk of inaction!** There may be aspects of life where the risk from doing nothing really is zero, but security rarely falls into that category!

### Remember that Risks Grow!

On a very related note, when you run into the inevitable difficult choice, **always err on the side of stronger protections**!

Why? Because the bad guys forget nothing, and are always learning. The amount of harm attackers can inflict on the first day a vulnerability is discovered is nothing more than a baseline — the absolute best you can hope for is that no one finds any way to make better use of the issue ever, and that's not even vaguely realistic!

I always think of Bruce Schneier's pithy line:

> "Attacks always get better"

In my mind I used to think of that as *Schneier's Law*, but I've had to update my naming scheme because it turns out he already has an older law, so I suggest we all start calling this *Schneier's Second Law*!

In case you're wondering, Schneier's first law is the perfect argument against rolling your own encryption or other security algorithm:

> "Any person can invent a security system so clever that she or he can't think of how to break it."

So, **always over-defend**, and if the decision is **border-line, err on the side of taking action**. The chances are high that the problem is about to get worse than you think!

## React Fast, but also Pre-empt!

So far I've focused mostly on making decisions when something happens, in other words, reacting to some kind of change. Maybe it's the release of a new attack tool, the discovery of a vulnerability, the rise of a new attack technique, or maybe it's a change of circumstance (maybe everyone's just been forced to work from home with no notice, say 😉). It could also be the rolling out of a new system or service that will make people's lives better in some way, but also opens up new attack surfaces.

It's annoying, but in security, even the best prepared people will be forced to react to events on a regular basis. But, the more prepared you are the less often you'll need to react, and the less you'll need to do in haste. If you keep everything patched, and news comes out of a nasty exploit in active use that was patched last month, no problem! You do a quick check of your audit logs, verify the patch did get applied, and move on with you day!

### The Inverted Pyramid of Pain

LEFT OFF HERE!!!


Where to start is a big question — so big most people and organisations become paralysed by it, and simply fall back into a perpetual reactive mode. If you're lucky, you're reacting to warnings from security agencies and reports from auditors, but sooner or later you'll be reacting to attacks.

Some pro-active security hardening is easy and involves little to no pain, and some is effectively impossible. You might think the easy stuff is likely to have small rewards, so is probably not worth it, but you'd be utterly wrong — the easy things tend to have the biggest effect, and the hardest things, the smallest effect! You can diagram that as an upside-down triangle, with ease (lack of pain) on the vertical axis and reward mirrored around the origin on the on the horizontal axis. This makes for a fun slide in presentations, and is generally referred to as *'the inverted pain triangle'*.

The bottom line is wonderful — **do the easy stuff first** because it will give you the best results for your efforts!

## Make Choices

So you're all inspired to go do something, great, but now you're going to be faced with decisions — what's the right value for this setting? What permissions should I give this user/computer/network? You'll inevitably be making tradeoffs, and each situation is different, but some general guiding principles can help a lot.

### Minimise the Attack Surface

### The Principle of Least Privileges

### Think Defensively

## Spread the Word!

### Don't Moralise, Evangelise!

### 'See something, say something!'