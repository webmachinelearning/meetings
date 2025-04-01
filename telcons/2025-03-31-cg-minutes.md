## WebML CG Teleconference [EU-APAC] – 31 March 2025

### Agenda

[2025-03-12-cg-agenda.md](/telcons/2025-03-31-cg-agenda.md)

### Minutes

#### Participants

Anssi Kostiainen,
Domenic Denicola,
Tarek Ziade,
Christian Liebel,
Maxim Salnikov,
Zoltan Kis,
Adam Sobieski


#### Introductions


Anssi: Welcome to this is the EU and APAC timezone friendly WebML CG Teleconference.

... we have a bunch of EU-based participants, so this option caters to our participants on those timezones and APAC 

... We alternate between the AMER-APAC (Tue/Wed 00:00-01:00 UTC) and this EU-APAC (Mon 07:00-08:00 UTC) option to cater to our geographically diversified participants. Feel free to join the option that fits your schedule better.

Anssi: WebML CG chair, Intel, happy to see all the recent progress on new built-in AI APIs, new contributors joining the effort, and new ideas brought up

Domenic: Google Chrome, work with Etienne from the US timezone, significant spec experience, interested in built-in AI APIs, want to help with my spec experience

Tarek: Mozilla, located in Burgundy France, thanks for this EU-friendly timezone

... I'm working on Firefox AI Runtime that is based on ONNX Runtime, working on web extension APIs, address similar tasks to what Domenic is doing on built-in AI APIs, I think this CG is a great place to work together

Zoltan: working with WebNN at Intel, also been working with OpenVINO, and POCs on Chromium, interested in application side of AI, built-in AI APIs very interesting

Maxim: Microsoft, Oslo-based, working on AI on the Web, cloud and web apps, interested in dev productivity

Adam Sobienski: interested in AI in education space, proposed a new feature for Prompt API to be discussed today

Christian: (joined a bit later)


#### Proofreader API

Anssi: on this call I'd like to gather further input and understand the use cases, assess readiness for adoption as a CG deliverable

... the proposed API finds and corrects errors in grammar, spelling, and punctuation

... while browsers and OSes offer this proofreading capability to users, there's no programmatic JS API

Domenic: discussed initially on the AMER meeting, people were generally positive

-> https://github.com/webmachinelearning/meetings/blob/main/telcons/2025-03-12-cg-minutes.md#proofreader-api

Domenic: would like to incubate this API in this group

Anssi: Proofreader API is an early design sketch for a proposed new built-in AI API that examines text

... how much of this API can be polyfilled?

Dominic: can be polyfilled on top of Prompt API, but not sure we'd ship Prompt API right now

... can we start with task-specific AI APIs, because output is constrained, easier to reach interoperability

... we could maybe have a smaller model and every site would run it, but could be tricky

Tarek: we need to have a deeper look at this API, try to look at this before our next meeting

Dominic: Tarek, you have an approach where you download models for tasks people are interested in?

Tarek: we use Transformers.js, have a list of tasks where to do inference, anything interacting with LLM is text-gen task


Anssi: any browser positions yet for Proofreader API? TAG feedback?

... not a requirement, based on what I hear the Proofreader API is ready to be adopted into the CG as a new deliverable, it has:

... - real-world use cases valuable to users

... - demonstrated to be implementable

... - aims to produce a spec that allows interoperable implementation between multiple browser engines

... I'll start the process to adopt this API soon, there's a 30-day group vote

Tarek: do you have people from Apple?

Anssi: we have 6 Apple folks in the WG and 2 in the CG, Mike is very active in the WG, can check with him for his interest for CG incubations too


#### Writing Assistance APIs review feedback

Anssi: I was expecting to see initial TAG review feedback by this meeting, this API was assigned to the 2025-03-25 TAG breakout

-> https://github.com/w3ctag/meetings/blob/gh-pages/2025/03-24-agenda.md

Anssik: I checked with the TAG chair on status, it seems the review feedback not ready yet

Dominic: naming feedback from TAG has been addressed, privacy feedback has a PR:

-> https://github.com/webmachinelearning/writing-assistance-apis/pull/47


Anssi: any specific questions to the TAG at this point?

Domenic: interoperability, how to best test this API


Anssi: Since we have Tarek on the call, I wanted to check if Mozilla has further feedback on the Writing Assistance APIs?

... we received feedback from Brian of Moz:

-> https://github.com/mozilla/standards-positions/issues/1067

Tarek: the stuff we did with Web Extension is very new, so we did not have enough data to formulate a proper position, still the same position, WIP

... one API we look at is the Prompt API, it is closer to what we are doing right now

... on our side the intent is to make sure web developers can experiment with models they want, built-in AI APIs hide the model details

Domenic: appreciate Mozilla's feedback, also happy to hear the interest for the Prompt API

Anssi: WICG issue has some insightful feedback too, have we addressed all of it?

Domenic: Joseph's high-level feedback was should we have all these built-in AI APIs if we have the Prompt API?

... we responded we're not sure if we will have the Prompt API in the browser

... Kenji shared some feedback on these APIs too


... the Writing Assistance APIs spec is getting very complete this week, should be in good shape

-> https://webmachinelearning.github.io/writing-assistance-apis/

Domenic: remaining TODOs are add introduction section, otherwise pretty happy with the specification


#### Prompt API feature requests


##### Exposing max image / audio limits?

-> https://github.com/webmachinelearning/prompt-api/issues/84


Domenic: we added multimodel inputs, "two images, please compare them"

... what we figured out is, there are some limits, we only have context window to accept e.g. 10 images

... we throw if going above the limit, and you get an event if you go over, should we tell ahead of time "only 10 images"

... this model follows a strategy of some LLMs, other model architectures might work differently

... this issue is one of the several issues, would this be useful?

... we are the developers making this API, not using it -- is this API something web developers might find useful?


Anssi: the question on whether to add this specific feature reminds me of the Postel's law:

... "be conservative in what you send, and liberal in what you accept"

... also Joshua Bloch's API design principle: "When in doubt, leave it out."

Domenic: I feel like leaving this out is better

... we had a partner for this API who wanted to display character counter

... that use case required this feature

Christian: the feature seems like a reasonable thing, if partners specifically need this, would be interesting


##### Multimodal real-time capabilities

Anssi: a feature request from Christian, Domenic was looking for JS API proposals for this

Christian: we're reviewing similar cloud-based APIs, on-device is about 1 year behind cloud-based

... Prompt API surprised people 1 year ago, multimodal demos where we upload an image of a car and can see damages, surprised people a year ago

... now real-time APIs are topical, "talk to your model", new use cases and scenarios

... conversational interactions, and tool-calling

Tarek: have you considered hybrid approach?

... interacting real-time with LLM, it feels like this is partially solved by speech-to-text, how about hybrid approach, easy tasks locally and hard things on the server?

Domenic: we are considering hybrid so that there's a fallback, a thin shim that falls back to server

... I agree with Christian, we're 1 year behind, due to development velocity, also models need to get smaller for on-device use

Christian: I can share a demo, OpenAI real-time API

[ Christian shares a web app demo of an insurance claim filled in with voice interaction only. ]


##### DOM integration

Anssi: a feature request to extend multimodal support to DocumentFragments that represent a minimal document object that is not part of the active document tree, changes to it don't affect the document

-> https://github.com/webmachinelearning/prompt-api/issues/70

[ Adam presents slides: https://github.com/user-attachments/files/19528026/Prompt-API-Plus-DOM.pptx ]

Domenic: thank you for the presentation, two high-level points

... 1) this goes straight to the proposal, would like to start with use cases, what product requires this that cannot be done with what we have now?

... 2) LLMs operate on text, what if you just feed in the HTML text, if you do .outerHTML you might get the results you want
... if you put metadata, LLMs understand the tag semantics, if we accept doc fragments we'd translate them to text under the hood anyway

Christian: it's an interesting proposal, would add to what Domenic said, would like to look at this from a broader scale, Agentic AI space, also question about serialization, useful on a broader scale, that may be too broad a topic for this group

Domenic: serialization of prompt, or format we input to the model, what is now an industry standard input might be better than what we use now

Adam: thank you for the feedback, I will follow up on the issue


Anssi: thank you all for joining us today, happy to see this active discussion!

... we will continue these EU-timezone friendly meetings, next up approximately 1 month from now
