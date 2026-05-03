+++
date = '2026-05-03T12:00:00-04:00'
draft = false
title = 'Building With Claude Design'
+++

# Intro

Over the past couple of weeks I have been spending time in the Claude Design preview, and the thing I keep coming back to is this: design is now accessible to anyone willing to spend a weekend playing around in it. I have always considered myself a backend developer, but Claude Design has changed how I think about the boundary between writing software and designing it. This is a tactical post about what I have actually been building with it.

# Redesigning the Reminiscence Agent UI

The first project I put through Claude Design was the dementia reminiscence agent I built during the Google hackathon. The UI I shipped during the hackathon was functional but rough, and I had been wanting to take another pass at it. I gave Claude my existing UI as a starting point and asked it to upgrade the design. Once I landed on a version I actually liked, I had it generate a design system for the rest of the app — colors, typography, components — so the whole experience could be brought up to the same level. The quality jump was big, and that really matters for an app whose users are elderly. Simple, clean UI is not optional in that context. It is the product.

I also used Claude to make a PowerPoint to showcase the app to a group of medical professionals. Same pattern — feed it the substance, let it handle the visual presentation. The slides were ready in a fraction of the time it would have taken me on my own, and they held up in front of a real audience.

# Designing a Prototype From Scratch at DCS

The other project where this has paid off is a prototype I am building from scratch at DCS. Here Claude Design has been even more efficient, because I was not asking it to scan a large existing codebase to understand context. I was just answering its questions about what I wanted, one at a time, and watching the design take shape. That kept my token usage low and the iteration loop fast — which matters during the preview, where rate limits are tight.

# What I Like

A few things have stood out as I have been using it:

1. It is a great on-ramp into design for someone who never went deep on it.
2. This is the AI-driven design format I have been wanting. I have tried tools like Google Stitch and bounced off — generating static photos is not what I need. Claude Design produces something I can actually iterate on inside a real workflow.
3. It is good for more than UI and UX. PowerPoints, videos, and other visual deliverables work well too, as long as you bring high-quality content for it to work with.

# What I Do Not Like Yet

It is a preview, so I am holding the rough edges loosely, but two things have bitten me:

1. Claude Design has its own rate limit, separate from the rest of Claude, and you can burn through it quickly. Worth knowing before you start a long iteration session.
2. I cannot manually edit a design once it is generated. If I try to tweak something by hand, the change gets sent back to Claude to redo, which uses tokens I was trying to save.

# Wrapping Up

Despite the rough edges, I am really excited about this. The bar for entry-level design work just dropped to a weekend of playing around, and that opens the door for a lot of people — myself included — who would not have called themselves designers before.

- Zachary Witte
