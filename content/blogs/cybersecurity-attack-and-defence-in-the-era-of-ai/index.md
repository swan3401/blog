---
title: "Cybersecurity: Attack and Defence in the Era of AI"
date: "2025-06-20"
draft: false
tags: ["Cybersecurity", "Ethics"]
categories: ["Activity report"]
description: "This post is based on webinar that brought together cybersecurity and AI experts to discuss the evolving threat landscape around artificial intelligence as it becomes increasingly integrated into business operations."
featured: false
---

## Introduction
I attended a webinar that brought together cybersecurity and AI experts to discuss the evolving threat landscape as artificial intelligence becomes increasingly integrated into business operations. The discussion has shown, that while AI introduces new attack vectors and challenges, many fundamental cybersecurity principles are still applicable. Key themes included the knowledge gap between data scientists and security professionals, governance requirements, and the inadequacy of current regulatory frameworks to keep pace with the growth of technologies, including AI.

## Speakers
- __Michael Argast__, CEO of Cobalt.io - Provides penetration testing services that helps organizations identify security vulnerabilities
- __James Stewart__, CEO of TrojAI - Specializes in cybersecurity solutions designed for AI systems
- __Matt Cooper__, Director of Governance, Risk and Compliance at Vanta - Works with automated security compliance processes and vendor risk management
- __Amir Feizpour__, Founder of Aggregate Intellect - Consultancy helping businesses integrate AI technologies into their operations

---

## AI Adoption Considerations
__Michael Argast__: Amir, what should organisations consider when adopting AI technologies?

__Amir Feizpour__: The lay of the land hasn't changed as much as it seems. The same traditional concerns remain, such as the risk of prediction errors during production, reputation risk, and data privacy and security. Obviously, there are a few new things in the mix, such as the unpredictable behaviour of LLMs or similar systems. These are the same types of concerns that we've had over the last decade or so. Robustness is now more important than ever.

> In AI, robustness refers to a model's ability to remain reliable under unexpected conditions, such as slightly noisy inputs, missing features (e.g. blurry images or background noise in audio), and edge cases (e.g. rare combinations of inputs or extreme values).

This is because we now have systems that are much more intelligent than those we have dealt with previously. We want to use them for a wider range of tasks that were traditionally reserved for humans. It takes much more time to think through and implement guardrails to guide the behaviour of these systems in a robust way that doesn't introduce new vectors of risk into the software being deployed.

## AI-Specific Threat Landscape
__Michael Argast__: James, I think safeguarding AI behaviour and the risks of its implementation is interesting, but your business is safeguarding the AI system itself. It's a different risk model in a way; it's got different risks and threats. What are some of the real threats that customers aren't thinking about?

__James Stewart__: Well, I agree with Amir that it's not necessarily about new concepts. We're seeing the same thing. We have clients who already have hundreds of models in production. I think what has changed is awareness of the potential threats surrounding AI models. These threats have come to the forefront.

> One of the challenges in AI security is the interdisciplinary nature of the threats. While traditional cybersecurity professionals understand network and application security and data protection, AI systems introduce mathematical and statistical vulnerabilities that require specialised knowledge.

There is a knowledge gap between data scientists, who train AI models, and cybersecurity experts. Data scientists do not learn how the systems they are creating can be exploited, and cybersecurity experts, who likely lack sufficient data science expertise, are not fully aware of how data science can be used against organisations.

Several AI threat frameworks have been introduced over the last few years: MITRE ATLAS, OWASP and NIST, for example. These frameworks highlight similar threat factors for LLMs, such as prompt injection, jailbreaking, denial of service, hallucinations and data extraction from the model. Threat vectors accompany models, and their number is limited only by the creativity of the actor trying to manipulate behaviour, really. This is what has worsened and how things evolved over the last few years.

__Michael Argast__: As a consumer, I don't know how to distinguish between a poorly trained model and a poisoned AI model.

> A poisoned AI model or data set refers to altered training data that causes the AI model to systematically produce incorrect assumptions. AI poisoning is intentional and targeted to achieve specific malicious outcomes. A poisoned model makes predictable and exploitable mistakes that benefit the attacker.<br>
For example, AI poisoning could make a spam filter ignore emails from a specific sender or cause AI-controlled vehicles to ignore road signs with a small sticker on them.<br>
Unlike traditional malware that can be detected through signatures or behavior analysis, poisoned AI models appear to function normally while containing hidden vulnerabilities.

__James Stewart__: It is very challenging to know if the model has been gamed. You can have naturally occurring adversarial influence. Security and robustness are two sides of the same coin. It is more difficult to manipulate the behaviour of robust models. You can make the model more secure, but this can actually hinder its accuracy.<br>
So, we've built a tool to pentest models and surface vulnerabilities and deficiencies, and then it's up to the organisation to determine whether the risk is acceptable given the value they are getting out of it.

## AI Governance and Risk Management
__Michael Argast__: Matt, how are AI security standards and governance different from the way vendor risk is governed with traditional SaaS platforms? What is different in the AI world, and what remains the same?

> Traditional vendor risk assessment focused on technical security controls and compliance certifications. AI introduces entirely new categories of risk that is not captured by existing frameworks.

__Matt Cooper__: Sure, good question. I'd also like to comment on your first question about what companies should consider when implementing AI. Many companies are dealing with AI, but not necessarily at the same level as James's customers. Many companies are introducing AI-powered features to their products, so concerns are more around data governance and privacy. These are traditional issues that have now been accelerated by AI.

> AI systems has created entirely new governance challenges. Organizations must now consider ethical implications, potential biases, and the societal impact of their AI deployments.

Returning to your question about governing AI, I would say that it's a whole new level of governance that doesn't really exist in cybersecurity. Specifically, I am talking about bias and hallucinations. These are entirely new domains that humans haven't really dealt with before. For example, voice cloning is not something you had to think about in traditional cybersecurity. Now, companies really need to consider who is involved, and cybersecurity teams probably don't have the full skillset required in legal and ethical domains.

## Building AI Security Capabilities
__Michael Argast__: Matt talked about the skills and resources required of a security team to assess AI. To me, it seems like a repeat of the transition to the cloud: organisations had to develop a new set of skills. One set of skills was about assessing cloud vendors, and another was about running and operating IaaS. Amir, you help organisations integrate AI into their products. As an organisation, can I just buy these off the shelf from you, or do I need to have a plan and build competencies internally?

__Amir Feizpour__: Yes, definitely. Very quick comment before we move on from ethics, legal and privacy. Definitely read how people are updating their terms of service. Companies are adding their AI features, but... Slack is a very good example. A few days ago, they announced that they were going to use all of their users' conversations to train their models and gave users the option to opt out. This created a bit of... 0_o (a stir), and it's important to be aware of this. For the longest time, SaaS meant "here is some software; you own the content and can do whatever you want", but now they're saying "by the way, a portion of what you were doing will remain in our system forever, and you can't stop us using it even if you don't like it". It's a very nuanced landscape, so you definitely have to keep your eyes open, because nobody is looking out for you :)

> The rapid pace of AI development means that traditional training and certifications are insufficient. Organizations must foster a culture of continuous learning and adaptation to keep pace with new threats and opportunities.

In terms of the skills necessary for companies, one of the most important things, even for AI engineers, is that the landscape is shifting so quickly that the most important skill for anyone these days is the ability to learn quickly. Knowing cloud, Python, or anything else is no longer useful. What matters is how quickly you can learn something that came out two weeks ago and deploy it right away.

A lot of what we do with clients is teaching them about phishing so their internal teams can get to grips with using these kinds of things. Ironically, this could account for up to 30% of the work I do, even though I never mention this aspect of my work. We run a number of workshops to teach them how these things work. (Intention here seems to be to highlight importance of understanding for the teams how AI can be exploited)

The decision between building internal capabilities versus outsourcing AI security functions depends largely on an organization's long-term AI strategy and the criticality of AI systems to their operations.<br>
If they want to operate their own models, the skillset needs to exist internally. There is a lot of information out there, so working with a partner who can point you towards the right curated information is very helpful. I think you need to pick a partner who can teach you about phishing rather than spoon-feeding you all the details.

## Regulatory Landscape
__Michael Argast__: One of the things I frequently hear is that AI is changing very quickly: new standards, new attack vectors and new models arising in every moment. Governments are trying to regulate AI, but they are really lagging behind when it comes to keeping up with technology. What are your thoughts on this? Can we trust in self-regulation of the industry?

__James Stewart__: The regulations are wonderful. The EU and Canada have outlined some pretty stiff penalties, but it remains to be seen what constitutes an offence. The value of regulations is that they are built on standards such as ISO. However, I think it is really up to organisations to manage their own risks, whether financial or reputational. Organisations want to avoid these risks. When Google introduced their LLM (Bard AI), there was a mistake in their marketing material, costing Google $100 billion in a single day. Therefore, the security team should move ahead regardless of where the regulations are.

> Traditional regulatory processes can take years to develop and implement and they are fundamentally mismatched with the rapid development of AI.

__Amir Feizpour__: I feel very cynical about how effective the regulations are. There has always been a gap between the boundaries of regulations and the edge of technology. The GDPR is a prime example. Europe did whatever it did; it had good and bad implications, and the rest of the world is still wondering what version to use. Now we're introducing LLMs, and in two years we'll have multimodal LLMs with significantly greater capabilities. I don't know what their answer is, but it doesn't look like the regulations are going to keep up — the gap is increasing. At what point will we be able to really regulate what is happening?

One interesting idea is to incentivise operations to be more responsible. Another interesting development around the market is the open source versus closed source. A bunch of companies have decided that their models should be closed source, while Meta and some others have decided that theirs can be open source. Creating these kinds of constructive tensions in the market is the way to go. Funding and empowering products that are privacy, responsible and secure by design, for example, is the right way to create an environment that encourages responsible deployment. Because creating red lines simply cannot keep up.

---

## Key Takeaways
- Read the terms
- If you are AI/ML engineer, try to stay current with rapidly evolving AI field
- If you are security professional, work closely with data science teams to understand model behavior and potential vulnerabilities
- If you are an organization adopting AI, develop teams that combine cybersecurity expertise with AI/ML knowledge
- If you are the AI business market, support the development of privacy-focused and secure AI solutions
- If you are the AI industry, don't wait for formal regulations; implement responsible AI practies proactively


