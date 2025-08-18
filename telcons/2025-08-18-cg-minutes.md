## WebML CG Teleconference [EU-Asia-Pacific] – 18 August 2025

### Agenda

[2025-08-18-cg-agenda.md](/telcons/2025-08-18-cg-agenda.md)

### Minutes

#### Participants

Anssi_Kostiainen,
Tarek_Ziade,
Brandon_Walderman,
Adam_Sobienski,
Zoltan_Kis

[Anssi acknowledges some participants are on vacation so feedback via GH is preferred especially for Built-in AI APIs topics ]


#### TPAC 2025 F2F announced (Kobe, Japan, 10–14 Nov 2025)

Anssi: TPAC is the W3C's annual all-groups meeting, for both Working Groups and Community Groups

... the TPAC 2025 plan for the WebML community is as follows:

... Monday 10 November 2025, 09:00–16:45 Japan Standard Time

... Monday 11 November 2025, 09:45-18:00 Japan Standard Time

... in the agenda you see Monday for WG and Tuesday for CG, but I'm proposing we'll use the time flexibly as to minimize scheduling conflicts for participants

... I'm aware of Domenic's (Built-in AI APIs editor) scheduling conflict for Tuesday (overlap with WHATWG), if there are any other known scheduling conflicts please let me know

... the registration is now open, please complete it as soon as possible

... TPAC remote participants are also expected to register

... also note there's a discounted hotel rate available for TPAC participants

-> TPAC 2025 overview https://www.w3.org/2025/11/TPAC/

-> Registration https://www.w3.org/2025/11/TPAC/#registration

-> Hotel booking https://www.w3.org/2025/11/TPAC/venue.html

Tarek: I'll be with WebML groups

Brandon: Microsoft team will be there and Google folks


#### Agentic web & WebMCP

Anssi: a new agentic web workstream launched and the its first exploration is the WebMCP proposal

... WebMCP in abstract: "Enabling web apps to provide JavaScript-based tools that can be accessed by AI agents and assistive technologies to create collaborative, human-in-the-loop workflows."

-> WebMCP repo https://github.com/webmachinelearning/webmcp

-> WebMCP explainer https://github.com/webmachinelearning/webmcp/blob/main/docs/explainer.md

-> WebMCP proposal https://github.com/webmachinelearning/webmcp/blob/main/docs/proposal.md

Anssi: the scope of work in this initial exploration phase is an explainer document and a high-level proposal that explores possible API shape without going into spec details

... the initial explainer and proposal is based on contributions by Microsoft ("Web Model Context") and Google ("Script Tools") and we've now completed the first part of merging the two proposals

... also open-source projects have informed the initial design and I want to acknowledge the following two projects specifically:

-> https://github.com/MiguelsPizza/WebMCP

-> https://github.com/jasonjmcghee/WebMCP

... I will initiate the Community Group charter change process soon to allow the group advance to the more formal specification drafting stage

... if you're aware of folks interested in contributing to this agentic web development, please extend my invite to them to join the Community Group:

-> https://webmachinelearning.github.io/community/#join

Tarek: Mozilla is scratching the surface of agentic web, we have three early prototypes ongoing

... I will read the WebMCP proposal and provide feedback

Brandon: WebMCP PR #3 (part 1) was to merge the explainer, there's some work on the API proposal

-> https://github.com/webmachinelearning/webmcp/pull/3

Brandon: it is not a spec yet, we start to converge across different teams now how the API could look like

... Edge's proposal is a little different from Google's and OSS projects'

... Alex's WebMCP OSS implementation experience would be helpful to capture in the repo, a starting point is here:

-> https://github.com/webmachinelearning/webmcp/blob/main/docs/explainer.md#webmcp-mcp-b

Zoltan: waiting to see how this works out, the proposal exposes tools and web pages act as MCP server

Brandon: page provides the tools, make requests to the backend server to fulfill the requests and present UI to complete the tasks, solicitation in real MCP terms

Zoltan: use cases could be improved to help readers focus on typical usages

Anssi: three use cases documented with user flows: Creative, Shopping, Code Review

-> https://github.com/webmachinelearning/webmcp/blob/main/docs/explainer.md#use-cases


Anssi: avoiding tight decoupling with MCP is a good design considering MCP spec itself is in flux

Brandon: initial drafts were even more decoupled from the MCP even the current protocol

... keeping MCP in the name helps ensure certain audiences will pay attention to this effort

Brandon: feedback received for WebMCP around security concerns

... there are ongoing MCP security incidents and folks have asked how we address this in WebMCP

... no great answers at the moment but will open a GH issue in the repo this week to discuss this with the community

... a top of mind topic is prompt injection and how to defend against malicious pages giving instructions that can be malicious

... a possible mitigation is to have agents be more vigilant

Anssi: the threats here differ from the traditional web security model, need domain experts for security insights


#### Prompt API - tool calling

Anssi: proposed new features related to tool calling:

##### Output schemas

-> https://github.com/webmachinelearning/prompt-api/issues/137

Anssi: the question is whether in addition to inputSchema, there should be outputSchema for tool calls for validation of structured results

... presumably outputSchema would follow the structure of inputSchema whose spec is WIP:

-> inputSchema https://github.com/webmachinelearning/prompt-api/#tool-use

-> https://webmachinelearning.github.io/prompt-api/#dom-languagemodeltool-inputschema

Anssi: apparently outputSchema is only defined in MCP:

... "Servers MUST provide structured results that conform to this schema."

... "Clients SHOULD validate structured results against this schema."

-> https://modelcontextprotocol.io/specification/2025-06-18/server/tools#output-schema

Anssi: I think we're looking for use cases, feedback in the issue welcome!

Zoltan: is the use case model chaining?

Anssi: probably yes, feel free to investigate this and share feedback in the issue


##### Return types

-> https://github.com/webmachinelearning/prompt-api/issues/138

Anssi: this is question about tool-call return type and its future proofing

... currently the type is always a string and objects are converted to strings "[object Object]"

... per research OpenAI and Vercel AI SDK return strings only

... MCP returns both type and text, so that'd be an array of LanguageModelMessageContent

-> LanguageModelMessageContent https://webmachinelearning.github.io/prompt-api/#dictdef-languagemodelmessagecontent

Anssi: feedback on this wanted, especially developer experience on ergonomics

... if the return type is always a string then developers can skip JSON.stringify() step

Zoltan: it is hard to standardize return types

Anssi: I think we want to understand what is the 80% solution and design for that and understand what is required for end to end flow with types

Tarek: in our side we have one use case where we call LLM and have the LLM ask the browser about some information in browsing history to improve the prompt and do some interactions

... struggling how make chaining work well for security reasons

... how to secure all these interactions

Zoltan: in this case it is in application domain?

Tarek: when the LLM calls back and asks for that information, how do you make sure you restrict what LLM can do?

... we want it to be automated, not always to have user in between, how to do that in a generic way

Zoltan: PING people would say implementation can't probe user's history

Anssi: is there a WIP feature for Firefox?

Tarek: it is a prototype and internal only, for the next meeting I can present a proposal, we're prototyping with OpenAI API

... discussion on Prompt API would help and privacy and security are biggest concern


##### Tool choice

-> https://github.com/webmachinelearning/prompt-api/issues/140

Anssi: a proposal from Vercel AI SDK contributor:

... "toolChoice" option to tell the model if it should use tools or not

... in the comments Sushanth shares Edge team's perspective that underlying model Phi4 does not explicitly support gradations in tool calling eagerness

... but notes this could be achieved with a system prompt and the proposed "toolChoice" parameter could change that system message -- more analysis needed

... feedback welcome in the issue on use cases that'd benefit from forcing the model to use tools (that may result in the model asking additional questions)

Tarek: can web search be a tool for Prompt API?

Anssi: I believe so, an implementation detail

Zoltan: suggest pre-mature standardization for Prompt API options to be avoided


#### Writing Assistance APIs

##### Device constraint API

-> https://github.com/webmachinelearning/writing-assistance-apis/issues/77

Anssi: motivation for the proposed constrain API:

"Chrome is currently working on making its models work on the CPU, instead of being restricted to devices with GPUs. This will expand the number of devices which can access these APIs. However, it will also open up the possibility of these APIs being slower for those new users, which the web developer might not anticipate or prefer"

Anssi: example: test whether a GPU model is available and only create the summarizer if it can be done on the GPU

... in GH comments Domenic notes he thinks the initial proposal in the issue is not quite right due to:

... - should be sensitive to various implementation architectures

... - cloud-based implementation considerations

... again, feedback wanted in the issue

Anssi: this proposed feature is similar to WebNN earlier MLDeviceType feature and has similar constrains and concerns

Tarek: why this feature is only for Writing Assistance, sounds very generically useful?

Zoltan: this is indeed a generic feature

Tarek: for our extension we added a backend option to select what backend is used

... do we have a spec for high-level generic features?

Anssi: not for AI features right now, but we've uses this pattern in aother domain: a Generic Sensor API is an abstract base class for shared generic features extended by concrete sensors building off that generic base

Tarek: we are interested in finding the best concurrency level for our features, to know the number of dedicated cores

Anssi: are you currently using .hardwareConcurrency?

-> https://html.spec.whatwg.org/multipage/workers.html#navigator.hardwareconcurrency

Tarek: initially we tried to use this API to come up with best number of threads to do AI

... but hardwareConcurrency does not give details on type of cores being used, e.g. low power, high performance

... if you don't have that level of detail it is hard to get to best result

Zoltan: thanks for noting this feature, TPAC discussion would be beneficial

Tarek: would like to have a TPAC discussion or a breakout session on this feature

Anssi: to conclude, we seem to agree this is a more of a generic feature than something useful for Writing Assistance only and this would warrant its own discussion, possibly a TPAC breakout


#### Proofreader API

Anssi: Proposed new features:

##### Confidence scores to output

-> https://github.com/webmachinelearning/proofreader-api/issues/18

"It would be helpful for each ProofreadCorrection to include an optional confidence field (e.g., a float between 0 and 1) indicating the model's certainty in its suggestion. This can support better UX decisions, like when to auto-apply a correction or show it as optional or filter out."

Anssi: no feedback yet, please chime in on GH issue with any feedback


##### User-provided custom dictionary

-> https://github.com/webmachinelearning/proofreader-api/issues/20

"This proposal suggests adding support for a user-provided custom dictionary to prevent the proofreader from incorrectly "correcting" these specific terms. This aligns with the "Alternatives considered" section, which mentions deferring this feature, and serves to formally open the discussion."

Anssi: use cases documented in the issue: technical jargon, brand/product names, acronyms

... proposed solution to pass an optional customDictionary dictionary into Proofreader.create() method with an array of string containing custom dictionary words

... similarly, will get back to this proposed new feature when the spec work on this ramps up after the vacations


##### AOB

Tarek: Flower.ai, Flower Intelligence is their library

-> https://flower.ai/intelligence/

... interesting feature of Flower.ai is that they provide e2e encryption for doing AI in the cloud

... call goes to server side with guarantees it won't be seen, aka confidential compute

... used by Mozilla Thunderbird to summarize emails

... they would have wanted to run things locally but found frustrating bugs in WebGPU

... unique to this API is it can fall back locally

... I could present about this in our future meetings

Anssi: this work is relevant to the group given it is allows switching between local and cloud compute, you're welcome to give a short presentation

... thanks for joining, we're back with the EU call in a month!
