## WebML CG Teleconference [EU-APAC] – 26 May 2025

### Agenda

[2025-05-26-cg-agenda.md](/telcons/2025-05-26-cg-agenda.md)

### Minutes

#### Participants

Anssi Kostiainen,
Domenic Denicola,
Tarek Ziade,
Zoltan Kis,
Rhys Jones,
Thomas Beverly

#### Prompt API implementation experience from AiBrow

Anssi: please welcome guest speakers: Rhys & Tom of the AiBrow project

... I've asked Rhys and Tom to give an intro and share learnings from AiBrow, a Chrome extension that implements the Prompt API and select other built-in AI APIs

... AiBrow uses llama.cpp web extension, WebGPU API, and native Chrome AI engine, supports custom models

-> https://github.com/axonzeta/aibrow

Anssi: a lot has happened over the last week in the built-in AI APIs space, Prompt API for Extensions ships in Chrome and previews in Edge

... Rhys & Tom built this AiBrow extension that extends the built-in AI APIs with new features for the Prompt API, such as:

... - structured output -> https://docs.aibrow.ai/examples/getting-json-output

... - custom models -> https://docs.aibrow.ai/examples/using-different-models

... - embeddings -> https://docs.aibrow.ai/examples/embedding-api

... custom models has been one of the early feature requests for the Prompt API, looking forward to further work on that in this group

-> https://github.com/webmachinelearning/prompt-api/issues/8

Anssi: design goals of AiBrow seem to align with those of the Mozilla's extension-based API proposal:

... - being able to select an exact model from a model hub as a key feature

... - consider installing an add-on to indicate to the user that they are stepping outside the bounds of normal web functionality

-> https://github.com/mozilla/standards-positions/issues/1213

Rhys: worked on AI browser Wavebox, for local web agentic features

-> https://github.com/wavebox/waveboxapp

Rhys: involved with OSS projects over the years

... thought local LLM support in browsers would benefit Wavebox

... thought best is to jump in and implement something and provide that implementation experience to help inform the API design

Tom: we started AiBrow around 9 months ago, exclusively web extension

... based on feedback from people there was friction with using WebGPU alone

... what we have is a layered approach, WebGPU extension, AiBrow extension

... we played with structured output API and grammar that we added early on

... we also added embeddings support

Rhys: we build on the shoulders of giants: lllma.cpp runtime, node-llama-cpp, node.js bindingd sfor llama.cpp

... as the API solidifies, there will be more implementations

... different use cases, drive-by web with minimal download, and SaaS tools that download an optimized binary

... along the spectrum there's different user demand, even if the API is the same

... the user needs local execution, while commercial use cases benefit from being able to offload the LLM cost

... there's also privacy benefit

... we can extend this approach to local network, natural rooting point

... using graceful degradation, if the local machine is not capable, can offload the workload to the cloud

... privacy is one of the features users like

... permissions is another thing we played with

Tom: we took camera and mic permissions where the domain requests this first

... if the user installs the extension can use the default model

... if the site wants to download another model, we introduce a permission prompt

... "Website wants to use X model"

... also user feedback was that we need download progress signals

... user frustration when the initial Google implementation did not disclose download progress

Rhys: models have different licenses, sometimes custom license needs to be surfaced, we make sure all the compliance issues are addressed

... fingerprinting mitigation means can't scan local models, needs to be gated behind a prompt

Domenic: AiBrow is great stuff, would be great to have Tarek's feedback from Mozilla who's been working on a similar extension

Rhys: the increased momentum from Chrome is great to see, more user validation for these usage

... we want to understand how to handle custom models and surface that

... we observe fine-tuned LoRA layers, with smaller models with fine-tuned LoRA gives better performance

... more of an industry question is, where do these models reside, how to build trust?

... in extension stores, with approvals and reviews, in Microsoft's Store, Google's Store?

... we do not want to store multiple models on the same machine, we do not want currupted models, tainted models

... have HF Hub integration

... what is Google's view into user's allowing to download the models?

Domenic: Summarizer uses LoRA under the hood, with fine-tuning works way better

... on custom models, two things:

... 1) where to distribute them

... 2) working with Mozilla on their standards position, we've done case studies with users

... anything we can do in this CG to make the APIs work with any model, we should look at that

... hard questions are: model trust and shared models

... Chrome is very unsure about the answers to these, Firefox wants the ecosystem to decide

... Google is cautious of letting Chrome use a lot of user's disk space

... for bigger things, or smaller things want to see a system that encourages some level of consolidation

... "please give me image segmentation" and "store" gives the best model for the task

... "give me a summarizer" so the implementation gives the best model for that task

... if I had to guess, it'd be a community curated list that tries to map device capabilities to models

Rhys: in terms of what quick wins are

... partition models on top of a core model

... interesting thing is, what is the discussion in 1-2 years when we have even better quantized models

... we're thinking of newer and better models, the benefit for using llama.cpp inference runtime

... there's advanced HW capabilities in latest devices from e.g. Apple, Intel, AMD to accelerate these workloads

... but also less capable machines can run some models, but different ones, for the same tasks

... how do you give that feedback to the developer to match hardware capabilities with models?

Anssi: thank you Rhys, this is similar to how the open web platform can adapt to both low-end and high-end devices, different form factors, given AI tasks are demanding for now, this disadvantages low-end currently, likely to change with time

... I'd like to ask Domenic for Chrome's view on how to support its billions of users with these built-in AI APIs, currently desktop-only

Domenic: in terms of current plans, we want to support Android as well, also Pixel phones

... the longer tail is harder, we are now working on CPU-only inference

... maybe half of the device population is not capable for running built-in AI APIs right now

... probably just need to wait for models to get better, and hardware as well

[ Tarek joined ]

Anssi: welcome Tarek, we'll do a quick recap of AiBrow that has a similar design direction to Mozilla's extension proposal

[ Rhys: recaps AiBrow ]

Tarek: the key thing for Mozilla is we want to be able to run different models, not just LLMs

... we are experimenting with a new AI-powered smart tab groups feature in Firefox

-> https://blog.mozilla.org/en/firefox/tab-groups-community/

Tarek: we have use cases where we train the models in browser

... not a good fit for llamafile, the new version adds multimodality

-> https://github.com/Mozilla-Ocho/llamafile

Tarek: because we're not sure what happens in model architectures in 1-2 years

... want users to be able to experiment with these APIs

... feedback from the summarizer API from Google was, we don't know if it is mature enough to be a standard today

... for the web extension proposal, we want to make it a vessel to give people access to the capability

... web extension proposal is browser agnostic, we could ship a Wasm runtime for any browser to use

... not sure what are Google's plans for models beyond Gemini Nano

... it sounds like AiBrow is in a similar space to us

... Google uses Origin Trials to let developers to use the APIs early

... a problem from our view is the models are runtime-specific

... GGUF or ONNX weights are specific, hard to implement so that they works for everyone

Anssi: can you talk about Mozilla's approach to model management, Model Hub?

-> https://firefox-source-docs.mozilla.org/toolkit/components/ml/models.html

Tarek: Model Hub is a component inside Firefox, has an allow/deny list for models

... in HF Hub each model has an unique model, name, version, can be filtered by HF organization

... we have implemented a list of blessed organization, Hugging Face, Transformers.js, ONNX Community

... if there would be a rogue model, we can add it to a list that is not allowed to run in the browser

... if you try to run it, we can block it

... portability of the Model Hub into web extension is not clear yet, it is specific to Firefox now

... we consider attack vectors using MCP that could leverage rogue models

Anssi: how to best allow experiments such as AiBrow and Mozilla's extension proposal on top of built-in AI APIs?

Domenic: AiBrow and Mozilla extension include some risks, have a different namespace, polyfills

... we can't use the same namespace, so must be careful with namespace usage

... it makes sense to use the built-in AI APIs as the base, extend them with custom models

Anssi: do you have best practices for extending these APIs the right way, would it make sense to document how to extend these APIs the right way?

Domenic: avoid names clashing, use polyfill best practices in general

... add new methods under a namespace

... best practices for creating new APIs, use common conventions such as download progress etc.

... we haven't written a guide yet

... Embedding API is very interesting, I see Embedding.create() follows the pattern

Zoltan: for model security, do we want to establish a mechanism when using the 3rd party models, e.g. allow model watermarking?

Domenic: if we have custom models, they could do something unsafe?

Zoltan: could use watermarking to avoid tampering models, encryption has a similar problem

... breaking end-to-end security chain, need to be able for an app to connect to the trust chain

Domenic: it seems this comes down to who decides what model users are able to access

Zoltan: modified model can be used for out-ot-bounds attacks, or other ways to trojan the system

Anssi: Rhys, you had some enterprise use cases for AiBrow, do you want to share?

Rhys: here's one use case we have, from users's perspective

... "magic copy paste", use SaaS tool online, copy spreadsheet to a sales tool and a local LLM does the mapping of data

... maybe you extend the current trusted environment

... if using a sales CRM system, can download LoRA, trust the site, then can download LoRA in a trusted environment scoped to that domain only

... this is a big win for small model capabilities

... using the existing domain system for enterprise seems reasonable

Tarek: in Firefox 141 we allow users's manage local AI models the user has downloaded via add-ons manager:

-> https://windowsreport.com/firefox-lets-users-remove-on-device-ai-models-for-smart-tab-grouping-link-previews-more/

Tarek: we want people to understand what is running on their system


#### Proofreader API kick off

Anssi: last week we transferred the Proofreader API to this Community Group to open it up for wider community contributions

-> https://github.com/webmachinelearning/proofreader-api

Anssi: I'm happy to officially kick off work on the Proofreader API

... in the interest of time, I'm proposing we defer the full kick off to our next call

... meanwhile, all please familiarize yourself with the repo, file issues and submit PRs ahead of time

Domenic: Proofreader API is behind other APIs, kick off in Q2 sounds good to me

Anssi: I'll schedule that for the next meeting


#### Prompt API security and privacy

Anssi: the built-in AI APIs approach security and privacy considerations professionally, kudos to Domenic and the contributors

... the latest published are the responses to the Security and Privacy Self-Review, all please review:

-> https://github.com/webmachinelearning/prompt-api/blob/main/security-privacy-questionnaire.md

Anssi: these built-in AI APIs have a lot of shared infra, including security and privacy, currently documented in the Writing Assistance APIs spec:

-> https://webmachinelearning.github.io/writing-assistance-apis/#privacy

-> https://webmachinelearning.github.io/writing-assistance-apis/#security

Anssi: as discussed, we could establish a "Built-in AI APIs Infra/Commons" where to keep these shared parts

Domenic: or consolidate all repos into one

Anssi: yes, could use the HTML LS as a model too, and redirect the dedicated URLs to the right sections in the all-in-one built-in AI APIs spec

Anssi: Domenic, what are the biggest challenges for security and privacy, where the group should focus its review?

Domenic: Prompt API is similar to Writing Assistance APIs in this regard

... interop remains the biggest challenge


#### AOB

Zoltan: a very thought-provoking discussion on extensions running AI, thank you!
