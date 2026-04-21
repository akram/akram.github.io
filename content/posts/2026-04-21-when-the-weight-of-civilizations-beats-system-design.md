---
title: "When the weight of civilizations beats system design"
description: "Why most 'new' problems in IT are old problems in disguise—and what that means for AI agents."
summary: "A short essay on organisation darwinism: centuries of human coordination already shaped the patterns we now encode in protocols and law."
date: 2026-04-21
draft: false
tags: ["systems", "philosophy", "AI", "networking"]
---

**Note on authorship.** This article was drafted with the assistance of an AI system. The ideas and framing are the author’s; the model helped with structure and wording. The **prompt** used to generate this piece appears below verbatim.

{{< prompt >}}

> write a blog post titled: "When the weight of civilizations beats system design"
> mention first that the article is AI written, and give the prompt that I will give you here.
>
> The idea of the post should describe what I call "organisation darwinism" . Sometimes, when building (IT) systems we tend to try to reinvent the wheel. Bring some new concepts thinking that the problem is new; but human, remained humans for years, decades, centuries and milleniums. After fixing their basic needs, and because they are a social specie, they started to organised and fixed upcoming issues slowly within the same timescale: first and foremost: communication. transmit information (the I in IT) , save it, improve it, etc....
> Legal issues also arise very early with the central concepts of liability, accountability, empathy fariness, equity and justice.
>
> So, most to not say all of the issues that we are facing in today's complex AI + IT world have been solved and refined for centuries. TCP, HTTP and SMTP are the first things that came to my mind when I have seen the parallel in the begining of my carreer. TCP as protocol is built as language: a set of rule to communicate and not interutp, HTTP as a library and SMTP as a postoffice.
>
> AI Agents will not make an exception to that. So today that we are facing issues with Authentication and Access Control for Agents, I just want to have a look at what already exist

{{< /prompt >}}

---

## Organisation darwinism

When we build IT systems, we often behave as if the problem were invented last Tuesday. We mint new nouns, draw fresh boxes on whiteboards, and reach for greenfield designs—while the hard part was never the syntax of our favourite language. It was coordination among people who do not share one brain.

I call the longer view **organisation darwinism**: over millennia, after food and shelter, human societies repeatedly converged on the same pressures. We are a social species. We had to **communicate**, to **remember**, to **dispute**, and to **assign responsibility** when things went wrong. Those needs did not appear with Kubernetes. They appeared with the first market, the first contract, and the first time someone said, “You told me X, and I relied on it.”

The information age did not create information; it **scaled** it. The “I” in IT is still transmission, storage, and refinement of meaning—only faster pipes and cheaper clay tablets.

Law arrived early for the same reason protocols did: ambiguity is expensive. Liability, accountability, empathy, fairness, equity, and justice are not buzzwords from a slide deck; they are the accumulated answers to “what do we do when trust breaks?” Strip the branding from today’s AI governance debates and you will find the same questions courts and councils have been stress-testing for centuries.

## Familiar shapes in unfamiliar stacks

Early in my career, the parallels were almost comically literal. **TCP** behaves like a language you agree to speak: turn-taking, acknowledgements, retransmission when meaning is lost—rules so that two parties can finish a sentence without talking over each other. **HTTP** felt like a **library**: you ask for a named resource; you receive a version; caching and redirects are the shelves and cross-references. **SMTP** felt like a **post office**: routing, envelopes, delivery attempts, bounce messages—society’s oldest asynchronous job queue.

None of these are perfect metaphors, but they are not accidents either. They encode social habits: politeness, addressing, provenance, retry, and failure semantics.

## AI agents inherit the same inheritance

AI agents will not get a pass from history. When we worry about **authentication** and **access control** for agents, we are not facing a wholly new species of problem. We are facing delegated action, identity, least privilege, audit trails, and liability—topics that legal systems and enterprises have refined the hard way.

That is an invitation, not a dismissal. The work ahead is to **map** agent behaviour onto durable patterns: who may act on whose behalf, for how long, under what scope, with what evidence, and with what rollback when the agent oversteps. The answers will borrow from OAuth and OpenID Connect, from RBAC and ABAC, from policy engines and service meshes, from contracts and from operational practice—not because those tools are sacred, but because they are the sediment of many failures.

The weight of civilizations is not romantic nostalgia. It is **compressed trial and error**. Before we reinvent the wheel, we should read the manual that humanity has been annotating since before we had packets.

---

*If you are building in this space, the practical next step is simple: enumerate your agent’s powers the way you would enumerate API scopes; then ask who is accountable when it misuses them. The technology will change; the question will not.*
