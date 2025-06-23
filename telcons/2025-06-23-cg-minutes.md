## WebML CG Teleconference [EU-Asia-Pacific] – 23 June 2025

### Agenda

[2025-06-23-cg-agenda.md](/telcons/2025-06-23-cg-agenda.md)

### Minutes

#### Participants

Anssi Kostiainen,
Domenic Denicola,
Kenji Baheux,
Christian Liebel,
Rhys Jones,
Thomas Beverly


#### HTTP Archive's Web Almanac

Anssi: HTTP Archive's annual state of the web report welcomes feedback from this Community Group

... Christian leads the GenAI chapter of this report




Christian: Web Almanac is HTTP Archive's publication

... identifies trends on the web, data-driven approach, has various chapters, the generative AI chapter of interest to this group

... we crawl million of web sites and look at the data

... for this chapter we want to gather insights on GenAI usages and are currently in planning phase

... now need to define custom metrics from real websites by looking at public source code and HTML available to identify useful usage patterns

... we are also looking at model providers for remote APIs and how those endpoints are used

... we assign so-called analysts to various sections, please see the planning doc for details

-> GenAI 2025 chapter planning doc https://docs.google.com/document/d/1HpI_E35FU_vqsJlMEONnCyR5lAvzDwVkWBg3lIlwlvw

Christian: thanks to Kenji for noting the topics are not just GenAI

... we also include lower-level APIs such as WebNN and libraries built on top e.g. ONNX Runtime Web

... one analyst is looking at models used by web sites, llms.txt and mcp.json usage for tools

... meta tags for generated content, check for validness

... people in this group can support the effort by joining as an analyst

... the overview of the chapter is as follows: intro, cloud vs. local, local technologies (Wasm, WebGPU, WebNN), Built-in AI APIs, related runtimes (Firefox AI Runtime), generated content

... additional considerations: ethical, bias, hallucination, prompt injection

Anssi: thank you for sharing, this is important work

... I see you're using JS injection to run the custom metrics through WebPageTest.org to collect information about usage patterns and how the pages are built

... example usage:

-> Custom metrics https://github.com/HTTPArchive/custom-metrics/blob/main/README.md

Anssi: for built-in AI APIs this tools could check for e.g. usage of various API interfaces

... how does Web Almanac complement the data collected via Origin Trials?

Kenji: we track Built-in AI APIs sign-ups from Origin Trials and API usage

... not sure how much we can share in public

Dominic: Chrome use counters data is public but very low because we just launched

Anssi: Christian, are you also planning to use Chrome use counter data?

Christian: Almanac downloads the HTML and does text search

... that means some APIs can be in code but not called, a prior example is a YT embed that showed high usage for the Clipboard API

Anssi: Chrome folks, what would you like to see from Web Almanac report?

Domenic: information on popular polyfills, e.g. AiBrow

Tom: polyfill usage is an interesting and useful category to track, can help with feature detection

Kenji: MediaPipe usage would be interesting to track


#### New proposals

Anssi: a new proposal for a Fact-checking API from Adam

-> Fact-checking API https://github.com/webmachinelearning/proposals/issues/11

Anssi: quoting the proposal:

"Using combinations of local and remote artificial-intelligence services, end-users could more easily fact-check content that they are either reading or writing in a Web browser."

Anssi: this API is inspired by experimental features developed by WikiMedia:

-> Citation Needed https://meta.wikimedia.org/wiki/Future_Audiences/Experiment:Citation_Needed

-> Add a Fact https://meta.wikimedia.org/wiki/Future_Audiences/Experiment:Add_a_Fact

Anssi: WikiMedia prototyped these as Chrome extensions 

... for feedback on the API, please use the proposal issue

Kenji: as a user, I can definitely see the value of this proposal

... the concern is about quality of implementation

... it is not clear whether this can be implemented reliably with the models we have, in a way the API keeps up

Anssi: further feedback is welcome via the proposals repo


#### Proofreader API kick off

Anssi: a few weeks ago we transferred the Proofreader API to this Community Group to open it up for wider community contributions

-> Proofreader API https://github.com/webmachinelearning/proofreader-api

Anssi: I'm happy to officially kick off work on the Proofreader API

... this API comes behind the other built-in APIs, and benefits from common patterns developed for the APIs that paved the way

Domenic: thanks for providing a home for this new API

... this is behind other APIs in development

... partners are interested, this API is good bang for the buck since most browsers already ship basic spell checking and can have a spell checking implementation without LLM

... this provides grammar checking and other options on top

Kenji: this is now behind a flag in a dev trial

... if the quality is good want to do Origin Trial in Chrome 139

... feedback is very welcome

Anssi: I'd like to get early feedback from other browser vendors in this group, e.g. Mozilla has been active

Christian: we could consider to add this API to Web Almanac

Rhys: we implement in AiBrow new built-in AI APIs and match their API surfaces, we have different models to do different things


#### Prompt API

Anssi: this is a community debrief of recent new features and improvements to the Prompt API


##### Recent changes


###### Structured output improvements 

-> Structured output improvements https://github.com/webmachinelearning/prompt-api/pull/128

Anssi: motivation for this improvement was to fix an implementation bug in Chrome and Edge described in:

-> https://github.com/webmachinelearning/prompt-api/issues/125

Dominic: this is an interesting change, via implementation experience we discovered a bug

... via research we found this is a canonical problem

... JSON schema is hidden and thus we use extra tokens for schema

... the implementation hides this

... we allow opt out, to not send the schema, this has some precedent

... e.g. in OpenAI JSON mode before structure output you need to tell the model JSON is expected

... we don't add validation step


##### Prompt validation and canonicalization

-> Prompt validation and canonicalization https://github.com/webmachinelearning/prompt-api/pull/123

Domenic: this is writing down in spec format how we go through the prompts


##### Assistant prefixes

-> Assistant prefixes https://github.com/webmachinelearning/prompt-api/pull/124

Anssi: assistant prefixes, aka prefills, allow constraining responses by providing a prefix that will guide the LLM to a specific response format

... to do this, the proposal adds prefix: true to the "assistant" role message, see:

-> Explainer > Constraining responses by providing a prefix https://github.com/webmachinelearning/prompt-api/blob/main/README.md#constraining-responses-by-providing-a-prefix


Domenic: use case here is you want the assistant to continue from the string you gave it

... "prefix: true" indicates you want the LLM to continue with the same message

... useful for e.g. backtick-backtick-backtick JSON to continue with JSON

Anssi: we can learn what people coming from Remote APIs adopting Built-in AI APIs expect in terms of features, this is one such feature

... AiBrow feedback?

Rhys: not yet implemented, but behind the scenes being used


##### New issues

###### Tool/function calling

-> Tool/function calling https://github.com/webmachinelearning/prompt-api/issues/7

Anssi: recent activity with this feature, Domenic reviewed popular APIs from OpenAI, Anthropic, Gemini, Vercel

... a pattern emerged based on which a JS API proposal was crafted

-> https://github.com/webmachinelearning/prompt-api/issues/7#issuecomment-2942909973

Anssi: there's a spec PR from Microsoft for this feature:

-> https://github.com/webmachinelearning/prompt-api/pull/131


Domenic: thanks Christian for opening this issue a year ago!

... we have a good idea how the API should look like

... tool/function calling is a useful feature for LLMs

... in the readme we show how this could be realized by emulation using a calculator example

-> https://github.com/webmachinelearning/prompt-api#emulating-tool-use-or-function-calling-via-assistant-role-prompts

Domenic: a special token works better for interoperability

... Microsoft submitted a PR for the feature on how to specify this feature and is starting implementation in Chromium

... open questions are around error behavior and how to handle multiple request, e.g. what is the weather in three cities

... if people have use cases or considerations beyond the basics please let us know

... we're now actively prototyping and have added "ecosystem parity" label for features that other popular language model APIs offer

-> https://github.com/webmachinelearning/prompt-api/labels/ecosystem%20parity

Christian: thanks, this is a great feature to have and test with users, I support this

Rhys: very keen to see how this develops, I'm following it personally


###### Chat completions format

-> Chat completions format https://github.com/webmachinelearning/prompt-api/issues/120

Anssi: this issue is tracking https://standardcompletions.org/ for chat completion format pre-standardization

Domenic: there's a group of folks who don't like that HTTP APIs behave differently, started this effort

... even for tool calling there are params vs input schema differences

... this effort is trying to create some early specs to converge

... similarly MCP is Anthropic's website

Anssi: the GH repo for this effort is the place to watch

-> https://github.com/standardcompletions/rfcs/issues


##### Prompt API web extensions

Anssi: new Prompt(-like) API web extensions (e.g. [AiBrow](https://github.com/axonzeta/aibrow), [Mozilla's trial web extension API](https://github.com/webmachinelearning/proposals/issues/9)) extend the Prompt API baseline with new features.

... any user feedback and implementation experience good to shared?

Rhys: it's been fun to work on AiBrow

... we have a chunk of work on multi modal going on, AiBrow is now also in Mozilla Store

... we are iterating on the new proposed features, tool calling is the big thing, details underneath is important, e.g. parallel calls

... this hits complexity of models, an area of research, all the development happens in the open

... we have WaveBox browser that includes AiBrow

... we have the open-source web extension AiBrow and Chromium browser that will ship with AiBrow

... the different in our approach is we open up the model for developer

Tom: we are working with the Mozilla team, looking if we can use Mozilla's backend

Anssi: can you share a bit more on WaveBox?

Rhys: WaveBox (https://wavebox.io/) is a Chromium-based browser that bundles AiBrow, available on desktop Windows, Linux, macOS, paid subscription for pro features and teams

Anssi: all browser implementations are considered in standards process for implementation experience assessment, including WaveBox


#### Translation API

Anssi: I'd like to discuss Mozilla's Translation API explainer proposal, understand its use cases and requirements vs WebML CG's Translation API

... if there's overlap, is is reasonable to expect us to converge?

-> Mozilla's Translation API explainer https://github.com/mozilla/explainers/blob/main/translation.md

-> Related standards-position discussion https://github.com/mozilla/standards-positions/issues/1015

-> WebML CG's Translation API https://webmachinelearning.github.io/translation-api/

Domenic: Mozilla's proposals does fewer things, considers elements in the DOM

... it is a subset of the CG's API

Anssi: I propose we defer this topic to a meeting when we have Mozilla folks on the call


#### Upcoming meetings

Anssi: due to the upcoming holiday season in the Northern hemisphere we will skip over July meeting and will meet again in August

... I have also requested a slot for this group from W3C's annual TPAC 2025 f2f meeting that takes place in November 10-14, 2025, in Kobe, Japan, I will inform you of the meeting date when confirmed

... the first half of 2025 has been super busy with a lot of exciting developments, and the pace of development is further accelerating as we venture into the second half of 2025

... thank you for your contributions, everyone!
