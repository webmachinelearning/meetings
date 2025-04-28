## WebML CG Teleconference [EU-APAC] – 28 April 2025

### Agenda

[2025-04-28-cg-agenda.md](/telcons/2025-04-28-cg-agenda.md)

### Minutes

#### Participants

Anssi Kostiainen,
Domenic Denicola,
Tarek Ziade,
Kenji Baheux,
Adam Sobieski,
Christian Liebel,
Ningxin Hu,
Zoltan Kis,
Thomas Steiner

#### Proposed new Community Group deliverables

##### Proofreader API

Anssi: Proofreader API was discussed earlier, use cases and proposal considered fit for adoption into this CG

... to that end, I've initiated call for review for the charter update to adopt the Proofreader API into this Community Group

-> https://lists.w3.org/Archives/Public/public-webmachinelearning/2025Apr/0001.html

Anssi: what's the implementation status of the Proofreader API proposal?

Domenic: the API is behind a flag in Chromium

Kenji: the Chromium CL is under review


#### Local inference web extension

Anssi: next, Tarek will present another possible future work candidate: local inference web extension

Tarek: wanted to share this proposal with the group for feedback

[ Tarek presenting a Google Doc outlining the Goals and Proposal ]

-> https://docs.google.com/document/d/1jiPm4YH9ivMvjMIX8BBRghXegHt5YfllR0lnF6pKUwk/

[ Quoting the proposal doc: "A web extension could fill some of the gaps today and give us a way to quickly prototype and explore. The basic mechanism would be to inject an API into the window when installed, and pages that want to use it could add a banner with an install link to the relevant browser addon site." ]

Tarek: Mozilla wants to experiment with web extension to run inference with a local runtime

... in Firefox we have Transformers.js with ONNX Runtime backend that is used to run small inference tasks in the browser

... we are experimenting with a link preview feature in Firefox Nightly

... we've proposed a trial API for extensions, can enable an option to provide direct access to the API

... we realized this is a niche use case

... thinking how to leverage the wider community, idea is to propose a web extension that surface an API to any web page

... and can provide a banner to install the web extension and allow some API to run

... by doing this we provide a way for the browser to manage model fetching, cross-origin sharing, permissions

... we could widen the ability for our community to test the feature


Domenic: this Community Group is the right group of people cross-browsers for this exploration

... as for the Community Group process, CG is for hosting the explainer or proposal doc, code hosted in Mozilla's repo


Kenji: it would be useful if you'd describe more the problems this proposal solves, and priority of those problems

... and if possible, in the long term what is the ideal case

... keep this as extension API or use this as a tool to identify proper web platform APIs for the long run?


Tarek: the idea is to let web sites to experiment with this, understand what people might do with this feature

... not necessarily long term, ideally we'd have something on the browser level to satisfy the requirements

... for use cases, there's a gap in building web extensions only, people want to use such a feature for web sites


Anssi: Prompt API started as a web extension only, so could follow a similar path here to understand what could work in drive-by web context, for web pages

Kenji: structured output for the Prompt API helps with cross-browser compatibility making that API more feasible for web pages

... we are interested in solving some of the stated problems, for example ability to share a model across origins


Anssi: thank you Tarek for this proposal, please open a new issue for our proposals repo https://github.com/webmachinelearning/proposals

... this allows us to solicit feedback from this community, and after some iteration, we will revisit this for the next steps


#### Prompt API feature requests

Anssi: we have a few recent feature requests on our agenda today, some forward looking

##### An output language support detection option

-> https://github.com/webmachinelearning/prompt-api/issues/97

Anssi: the problem to solve: "there is no way for web developers to know what those supported languages are from the [Prompt] API."

... open question "the option would have no impact on the actual output language"

... "The actual output just whatever the model decides to respond with, given its current prompt history."

... proposal is to add a new "expectedOutputLanguage" option passed to create()

... I found this a reasonable proposal, but want to encourage the whole group to look into this

Domenic: developers say, we care that the output quality is good, we don't use the Prompt API if it does not support proper Japanese language, for example

... some sites have strict requirements

... idea is the developer provides a list of languages they support

... would love people's input on this

Kenji: this is in part also motivated by safety reasons

... we check if it is the language we support and that the safety is good

Domenic: one use case for web developer is to only use the API if it supports a given language

Christian: is this restricted to English?

Kenji: currently, but we want to extend to non-English languages

Christian: how to solve this is interesting, download the languages the user expects?

Domenic: currently we only test for English, so need to do language detection on output and fail if there's no English

... if we switch to a model where the API can report "no support"

Kenji: language detector should work with natural language, not JSON

Anssi: is one major use case to allow fall back to cloud-based API?

Domenic: yes, exactly

Thomas: we definitely see partners doing a desired language to English to desired language dance, with the Translate API

... for input and output, developers use translator API

Domenic: possible action items for folks who want to help, check the naming suggestions

... general support?

Anssi: have you identified any interoperability issues from implementations perspective?

Domenic: no issues identified so far


###### Multimodal real-time capabilities revisited

-> https://github.com/webmachinelearning/prompt-api/issues/80

Anssi: Christian provided an API usage sample to illustrate a typical use case: a real-time speech-to-speech conversation

... this requires bidirectional streaming of audio

... assumes low latency responses for human-like interaction

... requires also ability to interrupt with voice for more natural voice conversations

... this feature requires a multimodal model that support real-time text and audio processing, e.g. GPT-4o or Gemini 2.0? with native audio output

... I wonder if multimodal should be part of the Prompt API core feature set, or an extension of it?


Christian: real-time conversation use cases have strong developer demand

... future extension would be nice to have

... this changes the UX, one can talk and get responses back in natural language

... currently this requires a cloud-based API, compute capability

... we see this use case more and more, if this can be done on-device, it becomes very powerful


Domenic: appreciate the API usage sketch

... we're about 1 year behind native, so we haven't investigated this yet

... model sizes for real-time are not too big, there are already tiny and medium sized models

... this makes this possibly feasible, want to keep the issue open to solicit more input

... this API would need a separate chat session abstraction, separate from current API

... a lot of this is based on audio capture input

... there's a parallel discussion with the Web Speech API, all browsers implement tha API with cloud currently

-> https://github.com/WebAudio/web-speech-api

Domenic: Firefox and Chromium are interested in on-device implementation of the Web Speech API

... that API is very old, want to understand if the old API should be modernized to a new API style

... it gives permanent results, not a stream as modern APIs

... non-text-based APIs need more thinking to understand the use cases

... Web Speech API assumes it uses a mic input, not audio from other source like MediaStreamTrack

... should multimodel Prompt API be able to use user's mic?

Kenji: I want to find discussion on the latest enhancement

Anssi: please check the latest commits:

-> https://github.com/WebAudio/web-speech-api/commits/main/



###### Model Context Protocol support

Anssi: we discussed Model Context Protocol in the WebML WG meeting a few weeks ago and it was suggested the Prompt API would be the most likely extension point

-> https://www.w3.org/2025/04/10-webmachinelearning-minutes.html#369e

Anssi: Christian opened a new issue #100 for the Prompt API to assess feasibility of this possible future enhancement

-> https://github.com/webmachinelearning/prompt-api/issues/100

Anssi: MCP support issue #100 depends on function calling, issue #7

-> https://github.com/webmachinelearning/prompt-api/issues/7

Anssi: function calling for Prompt API has a separate issue that has received a lot of+1s, also questions on implementation feasibility

Anssi: MCP is "function calling with superpowers" or a standard way to connect models to data sources and tools

-> https://modelcontextprotocol.io/introduction

Anssi: MCP resembles the traditional client-server model:

... - MCP Server, where the tools live, e.g. local calculator or remote weather lookup, web search etc. can be localhost or remote

... - MCP Client, connector usually part of the AI Agent, finds available tools, formats requests, communicates with the MCP Server

Anssi: the MCP issue points to an example of an MCP server that provides browser automation capabilities

... this Playwright MCP Server uses Playwright library that automates browser tasks across Chromium, Firefox and WebKit

... example functions provided by this MCP Server:

... - browser_navigate - navigate to a URL

... - browser_choose_file - browser choose one or multiple files to upload

... - browser_click - perform click on a web page

... - browser_hover - hover over element on page

... - browser_type - type text into editable element

... etc.

Christian: MCP is the foundation for all Agentic AI

... connects LLM to different services

... [mcp.so](https://mcp.so/) lists some MCP Servers that exists

... all of this is in flux, currently stateful, stateless features are being defined

... Playwright example:

... LLM is not able to access just its word knowledge, but can do something

... agentic AI is reasoning and action

... we don't need actual code to do this, it's all natural language

[ showing an example of an agentic AI use case that updates speaker portfolio information on a web page requiring user login ]

Christian: is it feasible to connect Prompt API with MCP Server?

... a lot of security and privacy considerations surely

... or is an alternative way preferred, for example, allow only control of your own browser instance, interact with the DOM of your current page?


Zoltan: about MCP, the big question is what MCP API do we expose to the client code: setting up tools, orchestration, guardrails etc, or what part (of guardrails for instance) is controlled by the browser

... is MCP already capable of specifying a human in the loop step or set of conditions?

... I think the Agent runtime needs to support human in the loop


Domenic: tool use prerequisite seems useful, should look at that after multimodal

... MCP, still trying to understand what are the use cases for browser

... on a technical level, MCPs are written as localhost servers that control your browser, generally not something you want to expose to the open web 

... no sense what are the things between local servers and function calling?

... where does MCP sit in the middle?

Anssi: one interesting use case would be to automate some of the web-platform-tests that have required manual intervention

... I'd propose we keep on exploring this, and try to identify a subset that is both useful and feasible to expose to the open web




#### Wide review topics

##### Shared security and privacy considerations

Anssi: shared security and privacy considerations for both writing-assistance-apis and translation-api landed recently, great work getting this so well fleshed out this early in the incubation phase

-> https://github.com/webmachinelearning/writing-assistance-apis/pull/47

Anssi: one TAG member reviewed the PR carefully, provided great feedback, and the PR was merged

Anssi: Domenic, do you have any questions to the group, what is the plan for this shared spec infrastructure?

Domenic: not sure how to host the shared considerations? open to suggestions from the group

Anssi: there's some precedent with the Generic Sensor API that hosts similar shared considerations for Sensor APIs that built atop of it


##### Language Detection i18n issues

Anssi: this issue asks whether we should allow results that are less than "und" to be included?

-> issue https://github.com/webmachinelearning/translation-api/issues/51
-> PR https://github.com/webmachinelearning/translation-api/pull/52

Anssi: this questions received active discussion and also i18n group was engaged

... the proposed solution that was adopted was to exclude very low-confidence results

Domenic: this means the sum of all confidence values could be less than 1 

