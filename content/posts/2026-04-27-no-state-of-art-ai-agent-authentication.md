---
title: "There Is No State of the Art in AI Agent Authentication (And That's a Problem)"
description: "Why OAuth Token Exchange fails agents, why the agent identity debate is absurd, and why Power of Attorney models matter more than we realize."
summary: "On discovering we're reinventing square wheels while ignoring centuries of working trust models—and what Red Hat can do about it."
date: 2026-04-27
draft: false
tags: ["AI", "agents", "security", "identity", "authentication", "OAuth", "standards", "Red Hat"]
---

**Note on authorship.** This article was drafted with the assistance of an AI system (Claude Sonnet 4.5). The experiences, frustrations, discoveries, and conclusions are the author's; the model helped with structure, flow, and articulation. The **exact instructions** that produced this piece are in the collapsible section below.

{{< prompt >}}

> Let's write a blog post. Last week I tried to figure out what could be the state of the art for Authentication and Access Control for AI Agents. TBH, I felt that I was late trying to do that; not late as a late-comer, but late as someone who had to work on that area who has been sent to a few directions just like it was SSoT (Single Source of Truth) to finally discover 2 things: I haven't done my due diligence to challenge the implicit directions that were acknowledged into my team. Secondly, there are actually very down to the ground considerations and solutions that must be challenged and that much more legitimate people than me are still trying to defend.
>
> I want you to write a blog post about this aspects and develop my frustration and difficulties when having to prove that OAuth Token Exchange for Agents was not appropriate. And the second thing is the frustration to discover that people like Christian Posta are trying to advocate that agents must have an identity. This is really confusing to think about this discussion, when it actually seems really obvious. Looping to our previous blog post, that is frustrating because we are trying not to only reinvent the wheel, but also centuries of trust human processes that actually worked.
>
> The 2nd big frustration is related to the PoA model that I have worked on. It took me a lot of prompts to build up that one, before starting to have a satisfyingly challenged version https://github.com/akram/poa-delegation-model when I found, and that was actually relieving, that an IETF draft https://www.ietf.org/archive/id/draft-vattaparambil-positioning-of-poa-01.html published in 2023 was proposed (but expired). The frustration was even bigger when I have seen the recording on YouTube of the PhD student and her mentor defending the proposition at the IETF forum in 2024. That was so violent and lacking empathy, compassion and true technical criticism. https://youtu.be/12Sagg32HT8?t=2200 (keep timestamp for the YT video).
>
> So, long story short, there is currently no state and no art in that domain; which is becoming really urgent. In that case, I think that at Red Hat we do have an opportunity to build up a standard here by proposing an innovative AND comprehensive solution for that space. Identity for agents seems to me as an evidence; and so Power of Attorney authentication and delegation models should also emerge for the sake of humanity, safety, accountability and much more reasons that counts for us, humans.

{{< /prompt >}}

---

## Or: How I Discovered We're Reinventing Square Wheels While Ignoring Centuries of Working Trust Models

Last week, I decided to do what I should have done months ago: figure out what the **actual state of the art** is for authentication and access control for AI agents. Not what my team assumed. Not what the implicit direction suggested. Not what seemed like the "Single Source of Truth" we'd all nodded along to. The *actual* state of the art.

I'm not late to this space as a newcomer. I'm late as someone who *should have been challenging these assumptions from day one*.

What I found was both validating and deeply frustrating.

## The Token Exchange Theater

For months, I'd been implementing **OAuth 2.0 Token Exchange (RFC 8693)** for our multi-agent system. It works. Technically. You can make agents exchange tokens. You can scope audiences. You can validate JWTs. You can check all the boxes.

But here's the thing: **OAuth Token Exchange is a human-centric authorization pattern being forced onto agents**. And when you really think about it, that's absurd.

OAuth was designed for scenarios where:
- A human user delegates limited access to an application
- The user is present (or was recently present) to consent
- The delegation is time-bounded and revocable
- The trust chain starts with a human making a conscious decision

Agents don't fit this model. At all.

When Agent A calls Agent B, which calls Tool C, which needs to access Database D on behalf of User E... whose authority are we actually representing? Who consented to what? What happens when Agent A hallucinates and decides to call a tool it shouldn't? What's the audit trail? Who's accountable?

Token exchange gives us *plausible authentication theater* while fundamentally missing the point.

And the truly frustrating part? I had to **prove** this was inadequate. Build comprehensive documentation showing the gaps. Demonstrate the edge cases. Make the case that what we were doing—what felt like the "obvious" solution—was actually a square wheel we were trying to roll uphill.

## The Agent Identity Confusion

Then I encountered something even more bewildering: serious people, including respected voices like [Christian Posta](https://www.solo.io/), are *still debating* whether agents should have identity.

Let me be clear: **of course agents need identity**.

This should be obvious. It's Identity 101. If something takes actions, makes decisions, accesses resources, or represents authority, it needs:

1. A verifiable identity
2. A trust anchor
3. An audit trail
4. Accountability

We don't debate whether service accounts need identity. We don't debate whether IoT devices need identity. We don't debate whether microservices need identity (SPIFFE solved this years ago).

But somehow, when we add "AI" to the equation, we're back to first principles, relitigating settled questions.

Why?

I think it's because we're collectively making two mistakes:

**Mistake #1: Treating agents as magic black boxes** instead of what they are—software with non-deterministic behavior that acts on behalf of principals.

**Mistake #2: Ignoring centuries of human delegation patterns** that actually worked.

We have legal frameworks. Power of Attorney. Guardianship. Trusts. Delegation chains. Witness requirements. Revocation procedures. Audit trails.

These aren't just bureaucratic overhead. They're *battle-tested trust mechanisms* refined over hundreds of years of dealing with delegation, authority, and accountability.

And we're... ignoring all of it? Starting from scratch? Reinventing the wheel but making it square?

## The Power of Attorney Revelation

After months of struggling with this, I started building what I called a [Power of Attorney delegation model for agents](https://github.com/akram/poa-delegation-model). The idea was simple: formalize agent delegation the way we formalize human delegation.

It took countless iterations to build something that felt right.

Then I discovered something both validating and infuriating.

In 2023, a PhD student named Vattaparambil submitted an IETF draft proposing exactly this: "[Positioning of Power of Attorney (PoA) for Digital Delegation](https://www.ietf.org/archive/id/draft-vattaparambil-positioning-of-poa-01.html)".

The draft expired. No adoption. No follow-up.

Then I found the video of her defending this work at an IETF forum in 2024: [Watch at timestamp 36:40](https://youtu.be/12Sagg32HT8?t=2200).

Watch that timestamp. Watch how the committee responds.

It's brutal. Not in the "rigorous technical critique" way. In the "dismissive, lacking empathy, fundamentally missing the point" way.

A PhD student proposing a thoughtful framework for something we desperately need, and the response is... institutional inertia dressed up as technical skepticism.

This is how good ideas die in standards bodies.

## There Is No State of the Art

Here's what I've learned:

**There is currently no state and no art in AI agent authentication.**

Let that sink in.

We have:
- **OAuth** (designed for humans)
- **SPIFFE** (designed for workloads, not decision-making agents)
- **mTLS** (designed for point-to-point trust)
- **JWT** (designed for claims, not delegation chains)
- **RBAC, ABAC, ReBAC** (designed for static policies, not dynamic agent behavior)

None of these were designed for the world we're building. A world where:
- Agents make autonomous decisions
- Delegation chains span multiple organizations
- Actions are non-deterministic
- Accountability matters more than ever
- Humans need to maintain ultimate control

We're in a space where **there are no standards because we haven't agreed on the fundamentals**.

Should agents have identity? (Yes, obviously.)  
Should delegation be formalized? (Yes, obviously.)  
Should we learn from centuries of human trust models? (Yes, obviously.)

But "obvious" doesn't mean "solved."

## The Opportunity

Here's where it gets interesting.

The lack of standards isn't just frustrating—it's an **opportunity**.

At Red Hat, we're building real multi-agent systems. Right now. In production. We're hitting these problems *in practice*, not in theory.

We have a chance to:

1. **Establish agent identity as a non-negotiable requirement**
2. **Propose Power of Attorney delegation models** that actually work
3. **Build comprehensive, battle-tested solutions** that become de facto standards
4. **Lead the industry** toward sane, safe, accountable agent systems

This isn't just about winning a technical argument. It's about:

- **Safety**: Agents that can't be held accountable are dangerous
- **Accountability**: When something goes wrong, we need to know who authorized what
- **Humanity**: These systems serve humans; humans must remain in control
- **Trust**: Without proper delegation models, we can't build systems worthy of trust

## What Needs to Happen

We need to stop pretending this is solved. We need to:

1. **Acknowledge that OAuth Token Exchange is inadequate** for agent-to-agent delegation
2. **Establish agent identity as table stakes**, not a debate topic
3. **Formalize Power of Attorney patterns** for digital delegation
4. **Build comprehensive frameworks** that handle:
   - Delegation chains with clear authority
   - Revocation and time-bounds
   - Audit trails and accountability
   - Human oversight and control
   - Multi-organizational trust
5. **Submit to standards bodies** with the patience to see it through
6. **Build working implementations** that prove these models work

## The Path Forward

I'm done assuming someone else has figured this out. I'm done deferring to "what everyone's doing." I'm done implementing square wheels because they're what we have.

We're at Red Hat. We build open source infrastructure that becomes industry standards. We've done it before. We can do it again.

But this time, we need to move fast. Because AI agents aren't waiting for standards bodies to catch up. They're being deployed. Right now. Without proper authentication. Without delegation models. Without accountability.

And every day we wait is another day we're building on sand.

---

**The bottom line**: Agent identity is obvious. Power of Attorney delegation is essential. And we can't keep pretending that forcing human-centric auth patterns onto autonomous agents is "good enough."

It's time to build something better. Not because it's easy. Because it's necessary.

And because if we don't, someone else will—and they might get it wrong.

---

## Related Reading

- Previous post: [Power of Attorney Model: A civilizational approach for AI agent authentication](../2026-04-21-power-of-attorney-model-ai-agent-authentication/)
- GitHub: [Power of Attorney Delegation Model](https://github.com/akram/poa-delegation-model)
- IETF Draft: [Positioning of PoA](https://www.ietf.org/archive/id/draft-vattaparambil-positioning-of-poa-01.html)
- IETF Presentation: [YouTube recording at 36:40](https://youtu.be/12Sagg32HT8?t=2200)

---

*What do you think? Are we overthinking this, or are we finally asking the right questions? Reach out—I'd love to hear from others working in this space.*
