# WebML WG/CG F2F Agenda - TPAC 2026 (Dublin, Ireland)

> Archived from [issue #39](https://github.com/webmachinelearning/meetings/issues/39).

>[!IMPORTANT]
> ### **This agenda is now stable. Minor adjustments may still be possible.**
<!--
> ### **This is a Living Agenda. Content is subject to change.**
-->
<!--img src="https://www.w3.org/2026/10/TPAC/images/banner.svg" alt="TPAC 2026"-->
<img src="https://webmachinelearning.github.io/logos/webml/logo-webml-white.png" alt="Web Machine Learning">

# W3C TPAC 2026: Web Machine Learning WG/CG F2F

### Logistics

>- ✅ Registration: [is open](https://www.w3.org/register/tpac2026) (Standard fee until 01 October 2026) <!-- >>   - See also: [registration fee waivers](https://www.w3.org/2026/10/TPAC/registration.html#waiver) -->
>- 🏨 Venue: [Clayton Hotel Burlington Road](https://www.claytonhotels.com/burlington-road/), Dublin, Ireland in-person & remote
<!--
>   - Monday: 09:00–16:45 GMT, room `TBA`
>   - Tuesday: 08:30–15:00 GMT, room `TBA`
>   - All WebML WG/CG participants and invited guests welcome
-->
>- 📞 Remote joining instructions: see Invite > Joining Instructions (1 wk prior)
>- ✍️ IRC web client: [#webmachinelearning](https://irc.w3.org/?channels=#webmachinelearning)
>- 🗓️ Invites: [26 October 2026](https://www.w3.org/events/meetings/dfcd7873-1491-4b68-ae1c-fe3e54c849f0/), [27 October 2026](https://www.w3.org/events/meetings/dcb0ae4c-9f48-4210-b489-b051a8d35ad7/)
>- ✍️ Minutes: [minutes 26 October 2026](https://www.w3.org/2026/10/26-webmachinelearning-minutes.html), [minutes 27 October 2026](https://www.w3.org/2026/10/27-webmachinelearning-minutes.html), [minutes 30 October 2026](https://www.w3.org/2026/10/30-webmachinelearning-minutes.html)

# Agenda

<!--Feedback and suggestions for F2F topics welcome via comments for both `TBA` topics (To Be Announced) and timing to avoid scheduling conflicts. F2F issues are triaged as `Agenda+`.-->

## 26 October 2026: Working Group (Web Neural Network API)
<details close><summary>Toggle agenda ⤵️</summary>

Meeting schedule in [Greenwich Mean Time (GMT)](https://www.timeanddate.com/time/zones/gmt). Remote participants, please confirm your local start time using the timezone table below.

<details close><summary>See the timezone table ...</summary>
<table>
<tr><td> San Francisco <td> Mon, 26 October 2026 <td> 02:00
<tr><td> Boston <td> Mon, 26 October 2026 <td> 05:00
<tr><td> London <td> Mon, 26 October 2026 <td> 09:00
<tr><td> Berlin <td> Mon, 26 October 2026 <td> 10:00
<tr><td> Helsinki <td> Mon, 26 October 2026 <td> 11:00
<tr><td> Shanghai <td> Mon, 26 October 2026 <td> 17:00
<tr><td> Dublin <td> Mon, 26 October 2026 <td> 09:00
<tr><td> UTC <td> Mon, 26 October 2026 <td> 09:00 UTC
</table>

See also: [other locations](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20261026T09)
</details>

> Working Group [home](https://www.w3.org/groups/wg/webmachinelearning/) | [charter](https://www.w3.org/2025/03/webmachinelearning-charter.html)
>
> WebNN API [spec](https://www.w3.org/TR/webnn/) | [explainer](https://github.com/webmachinelearning/webnn/blob/main/explainer.md) | [open issues](https://github.com/webmachinelearning/webnn/issues) | [implementation report](https://wpt.fyi/results/webnn)

### ▶️ `09:00` (GMT) Welcome & direction

#### Intros & agenda bashing

Confirm the agenda and identify any attendance constraints.

#### Charter orientation

Current baseline, major milestones, expected changes.

- WebNN API 22 January 2026 CR Snapshot and Chrome/Edge Developer Trials
- API stabilizing, key breaking changes/new features since Kobe: minimum data types and rank ranges [PR #910](https://github.com/webmachinelearning/webnn/pull/910), initial WebGPU interop [PR #942](https://github.com/webmachinelearning/webnn/pull/942), and security limits [PR #926](https://github.com/webmachinelearning/webnn/pull/926) / [PR #933](https://github.com/webmachinelearning/webnn/pull/933)
- Status of Kobe resolutions: dynamic shapes [#883](https://github.com/webmachinelearning/webnn/issues/883), subgraphs [#907](https://github.com/webmachinelearning/webnn/issues/907), streaming constants [#901](https://github.com/webmachinelearning/webnn/issues/901), and compute policy [#911](https://github.com/webmachinelearning/webnn/issues/911)
- Charter next steps

#### Proposed breaking changes

Confirm the compatibility plan, owners.

- Unblock `MLComputePolicy` [PR #923](https://github.com/webmachinelearning/webnn/pull/923)
- Land the rank relaxation and operator renames from [#904](https://github.com/webmachinelearning/webnn/issues/904)
- Decide whether to remove constant tensor support [#940](https://github.com/webmachinelearning/webnn/issues/940)
- Discuss any blockers for the resolution allowing zero-size dimensions [#391](https://github.com/webmachinelearning/webnn/issues/391)

#### Device selection & effective compute policy

Converge on a proposal to develop, document considered alternatives.

- Compare the four [#934](https://github.com/webmachinelearning/webnn/issues/934) proposals: compilation/runtime metrics, latency vs throughput, strict hints, and `low-latency` / `precision` hints
- Decide how `intendedComputePolicies`, performance reporting, and the [DAOP incubation](https://github.com/webmachinelearning/daop) fit together
- Validate against use-case hints [#902](https://github.com/webmachinelearning/webnn/issues/902) and real-time workloads [#898](https://github.com/webmachinelearning/webnn/issues/898)
- Address privacy and fingerprinting concerns around effective policy or device exposure
- Related breakout: https://github.com/w3c/tpac2026-breakouts/issues/72

### ⏸️ `10:30` (GMT) Break

Drinks and snacks: Pre-function + Bbar, Ground Floor.

### ▶️ `11:00` (GMT) LLM enablement

#### Dynamic shapes

Discuss dynamic shapes implementation experience and any further spec refinements.

- Review [#883](https://github.com/webmachinelearning/webnn/issues/883) and dynamic-shape explainer [PR #945](https://github.com/webmachinelearning/webnn/pull/945) as appropriate
- Triage [PR #945](https://github.com/webmachinelearning/webnn/pull/945) questions on tensor-derived sizes, fingerprinting, and symbolic shape inference
- Compare Core ML and LiteRT implementability and prototype experience
- Define the security review needed for dispatch-time validation

#### Subgraphs & operator set

Define the minimum subgraph API experiment, JS examples, and performance evidence.

- Review the [#907](https://github.com/webmachinelearning/webnn/issues/907) proposal and Grouped Query Attention example
- Core operator set [#573](https://github.com/webmachinelearning/webnn/issues/573)
- Consider a loop operation for state-space models [#559](https://github.com/webmachinelearning/webnn/issues/559)
- Agree to not remove operators [#689](https://github.com/webmachinelearning/webnn/issues/689) before subgraphs exist and are measured

#### Low precision & quantization

Discuss new data types and quantization interoperability.

- Low-precision data types [#930](https://github.com/webmachinelearning/webnn/issues/930), explainer [PR #938](https://github.com/webmachinelearning/webnn/pull/938), and spec [PR #956](https://github.com/webmachinelearning/webnn/pull/956) next steps
- Agree criteria for adding data types and how unsupported types are reported
- Decide next steps for optional `zeroPoint` [#943](https://github.com/webmachinelearning/webnn/issues/943), Core ML constant-only constraints [#822](https://github.com/webmachinelearning/webnn/issues/822), and blockwise expansion [#903](https://github.com/webmachinelearning/webnn/issues/903)

#### New proposals

Introduce new proposals to fill in the gaps in LLM enablement.

- Build-time metadata [#965](https://github.com/webmachinelearning/webnn/issues/965)
- Stateful model [#966](https://github.com/webmachinelearning/webnn/issues/966)
- Related implementation experience: a dynamic language model (Qwen3-4B) on the Intel NPU via WebNN


### ⏸️ `12:30` (GMT) Lunch

Sussex restaurant + Bbar, Ground Floor.

### ▶️ `13:45` (GMT) Implementations & ecosystem

> WebNN implementation status by: [operations](https://webmachinelearning.github.io/webnn-status/#ops) | [frameworks](https://webmachinelearning.github.io/webnn-status#ops_framework) | backends [Lite RT](https://webnn.io/en/api-reference/browser-compatibility/litert), [Windows ML](https://webnn.io/en/api-reference/browser-compatibility/windowsml), [Core ML](https://webnn.io/en/api-reference/browser-compatibility/coreml) | [hardware accelerators](https://webnn.io/en/api-reference/browser-compatibility/api) | [architecture](https://raw.githubusercontent.com/webmachinelearning/webnn/refs/heads/main/content/webnn_arch.svg)

#### Demos & implementation status

Record interoperability blockers, implementation experience to inform specification priorities.

- Chrome/Edge Developer Trial/prototyping feedback [#964](https://github.com/webmachinelearning/webnn/issues/964)
- Firefox implementation hits a key milestone
- RustNN running BabyLM models on constrained devices
- More demos: [LiteRT.js integration](https://litert.webnn.io/), [NPU stem separator](https://microsoft.github.io/webnn-developer-preview/demos/stem-separator/), [Transformers.js demos](https://huggingface.co/webnn/spaces)
- Backend status: LiteRT, Windows ML, and Core ML

#### Customer stories

Select the highest-impact framework or model gaps to feed into the WebNN roadmap.

> See [WebNN Awesome](https://github.com/webmachinelearning/awesome-webnn) for community feedback, demos, presentations, samples, testimonials, tutorials, videos, and more.

- [onnx2webnn](https://github.com/rustnn/onnx2webnn): top-50 Transformers.js [model validation](https://github.com/rustnn/onnx2webnn/blob/main/docs/model-validation-status-triage.md) and [operator conversion](https://github.com/rustnn/onnx2webnn/blob/main/docs/operator-conversion-status.md)

#### Weights & memory

Discuss prototyping interest for streaming and caching, with agreement on measurements e.g. peak memory and startup time.

- Streaming constants and separation of graph build from weight loading [#901](https://github.com/webmachinelearning/webnn/issues/901)
- MLGraph caching [#807](https://github.com/webmachinelearning/webnn/issues/807)
- Relationship to hash-addressed [Cross-Origin Storage](https://wicg.github.io/cross-origin-storage/), without expanding WebNN's scope into a storage API

#### WebGPU interop v2

Agree the v2 API direction for device matching and usages, and identify any concrete cross-group coordination requests.

- `interopDevice` for zero-copy selection [#941](https://github.com/webmachinelearning/webnn/issues/941)
- Exported `GPUBuffer` usage flags [#954](https://github.com/webmachinelearning/webnn/issues/954)
- Timelines [#529](https://github.com/webmachinelearning/webnn/issues/529)
- Sample code [#343](https://github.com/webmachinelearning/webnn/issues/343)
- Coordination with the GPU for the Web WG

### ⏸️ `15:00` (GMT) Break

Drinks and snacks: Pre-function + Bbar, Ground Floor.

### ▶️ `15:30` (GMT) Security, Conformance & wrap-up

> WebNN [implementation report](https://wpt.fyi/results/webnn) | [WPT test suite](https://github.com/web-platform-tests/wpt/tree/master/webnn) | [webnn report](https://webnnreport.org/)

#### Security hardening

Confirm normative algorithms and owners for the remaining security-related spec and WPT changes.

- Relational limits for convolution and pooling [#928](https://github.com/webmachinelearning/webnn/issues/928)
- Refresh Security Considerations and out-of-bounds handling [#927](https://github.com/webmachinelearning/webnn/issues/927)
- <strike>Discuss full-sequence descriptor validation [#949](https://github.com/webmachinelearning/webnn/issues/949) / [PR #955](https://github.com/webmachinelearning/webnn/pull/955) as appropriate.</strike>

#### Numerics & WPT

Agree the normative-vs-test tolerance split and spec and WPT changes.

- Accumulator precision explainer [#948](https://github.com/webmachinelearning/webnn/issues/948)
- Trigonometric accuracy [#914](https://github.com/webmachinelearning/webnn/issues/914)
- Stable decompositions [#947](https://github.com/webmachinelearning/webnn/issues/947) / [PR #957](https://github.com/webmachinelearning/webnn/pull/957)
- WPT tolerances [#950](https://github.com/webmachinelearning/webnn/issues/950) and boundary classification [#960](https://github.com/webmachinelearning/webnn/issues/960)
- GPU-backed WPT runners update ([26 March resolution](https://www.w3.org/2026/03/26-webmachinelearning-minutes.html#cd01))

#### Issue triage slate

Check owners, interest, close or explicitly defer.

- Resolved but no spec PR: [#935](https://github.com/webmachinelearning/webnn/issues/935), [#919](https://github.com/webmachinelearning/webnn/issues/919) (#391/#904/#928 are covered in dedicated slots)
- LiteRT backend gaps: [#876](https://github.com/webmachinelearning/webnn/issues/876), [#877](https://github.com/webmachinelearning/webnn/issues/877), [#878](https://github.com/webmachinelearning/webnn/issues/878)
- Close candidates: [#853](https://github.com/webmachinelearning/webnn/issues/853), [#879](https://github.com/webmachinelearning/webnn/issues/879), [#124](https://github.com/webmachinelearning/webnn/issues/124), [#900](https://github.com/webmachinelearning/webnn/issues/900)
- Older interop backlog: [#180](https://github.com/webmachinelearning/webnn/issues/180), [#444](https://github.com/webmachinelearning/webnn/issues/444), [#481](https://github.com/webmachinelearning/webnn/issues/481), [#486](https://github.com/webmachinelearning/webnn/issues/486), [#487](https://github.com/webmachinelearning/webnn/issues/487), [#691](https://github.com/webmachinelearning/webnn/issues/691)

#### WebNN horizontals

Identify required horizontal reviews, owners, and supporting WebNN text or evidence.

- Privacy and fingerprinting risks from compute-policy, performance, and `opSupportLimits` exposure
- Sustainability impact follow-up [#861](https://github.com/webmachinelearning/webnn/issues/861)

#### Wrap-up

Confirm the resolution summary, next CR Snapshot target.

- Synthesis of resolutions, actions, known risks
- Next Candidate Recommendation Snapshot target

### To be triaged before F2F

Resolve asynchronously or bring to F2F agenda.

Possible additional topics: batched `gemm` [#929](https://github.com/webmachinelearning/webnn/issues/929), <strike>inferred convolution groups [#959](https://github.com/webmachinelearning/webnn/issues/959)</strike>, mixed-type `pow` [#939](https://github.com/webmachinelearning/webnn/issues/939), and custom operations [#6](https://github.com/webmachinelearning/webnn/issues/6).

### ⏹️ `16:45` (GMT) End

- 🍽️ Group dinner (venue `TBA`)


</details>



## 27 October 2026: Community Group (WebMCP, Prompt API, other Built-in AI APIs)
<details close><summary>Toggle agenda ⤵️</summary>

Meeting schedule in [Greenwich Mean Time (GMT)](https://www.timeanddate.com/time/zones/gmt). Remote participants, please confirm your local start time using the timezone table below.

<details close><summary>See the timezone table ...</summary>
<table>
<tr><td> San Francisco <td> Tue, 27 October 2026 <td> 01:30
<tr><td> Boston <td> Tue, 27 October 2026 <td> 04:30
<tr><td> London <td> Tue, 27 October 2026 <td> 08:30
<tr><td> Berlin <td> Tue, 27 October 2026 <td> 09:30
<tr><td> Helsinki <td> Tue, 27 October 2026 <td> 10:30
<tr><td> Shanghai <td> Tue, 27 October 2026 <td> 16:30
<tr><td> Dublin <td> Tue, 27 October 2026 <td> 08:30
<tr><td> UTC <td> Tue, 27 October 2026 <td> 08:30 UTC
</table>

See also: [other locations](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20261027T0830)
</details>

### ▶️ `08:30` (GMT) Start

#### Intros & agenda bashing

Confirm participants, scribes, agenda, and decision-making process.

#### WebMCP since Kobe

Establish a shared baseline for the day.

- Celebrate major spec progress since Kobe
- Acknowledge wide review, standards positions, implementation momentum
- Standardization path and the [Agentic Web WG Charter draft](https://w3c.github.io/charter-drafts/2026/agenticweb-wg.html)

#### API shape & multi-stakeholder support

Converge on the API direction and key design considerations.

- Generic communication and Tool-object direction [#236](https://github.com/webmachinelearning/webmcp/issues/236)
- API design questions: headless use, origin isolation, progress, and schema format [#237](https://github.com/webmachinelearning/webmcp/issues/237)

#### Tool discovery & cross-origin exposure

Agree the discovery and exposure model to develop.

- Discovery beyond one traversable navigable [#227](https://github.com/webmachinelearning/webmcp/issues/227)
- Host-controlled iframe access [#317](https://github.com/webmachinelearning/webmcp/issues/317) and cross-origin agents [#52](https://github.com/webmachinelearning/webmcp/issues/52)
- Security and Privacy: Two-sided opt-in [PR #326](https://github.com/webmachinelearning/webmcp/pull/326)

#### Declarative API next steps

Decide the home and maintenance plan for declarative WebMCP work.

- Spec [PR #338](https://github.com/webmachinelearning/webmcp/pull/338), native support concerns [#144](https://github.com/webmachinelearning/webmcp/issues/144), and JS-driven forms [#138](https://github.com/webmachinelearning/webmcp/issues/138)

### ⏸️ `10:00` (GMT) Break

Drinks and snacks: Pre-function + Bbar, Ground Floor.

### ▶️ `10:30` (GMT)

#### Developer feedback & ecosystem

Extract actionable implementation and developer feedback.

- [Origin Trial feedback](https://groups.google.com/a/chromium.org/g/blink-dev/c/lkdLdy5VPoA/m/Fdgc6AkbCgAJ)
- [WebMCP Challenge](https://openai.com/webmcp-challenge/) takeaways from the 5000+ submissions
- Current [implementation status](https://github.com/webmachinelearning/webmcp/blob/main/implementation-status.md)
- [WebMCP polyfill](https://github.com/w3c-oss/webmcp-polyfill/)

#### Cross-document continuations & page context

Align navigation continuity, tool stability, and page-context updates.

- Converge continuation designs: tokens [PR #327](https://github.com/webmachinelearning/webmcp/pull/327) vs `continueAfterNavigation` [#135](https://github.com/webmachinelearning/webmcp/issues/135)
- Tool stability [#328](https://github.com/webmachinelearning/webmcp/issues/328)
- Agent synchronization with page context [#312](https://github.com/webmachinelearning/webmcp/issues/312) and context loss on tool changes [#262](https://github.com/webmachinelearning/webmcp/issues/262)

#### Tool contracts: schemas, results, annotations

Agree on tool schema, result, and annotation semantics.

- `outputSchema` [PR #254](https://github.com/webmachinelearning/webmcp/pull/254) and [#9](https://github.com/webmachinelearning/webmcp/issues/9) closure
- Browser validation and the JSON Schema subset [#92](https://github.com/webmachinelearning/webmcp/issues/92)
- High-risk reads [#331](https://github.com/webmachinelearning/webmcp/issues/331)
- Input length limits [#73](https://github.com/webmachinelearning/webmcp/issues/73), text units [#219](https://github.com/webmachinelearning/webmcp/issues/219) and [PR #265](https://github.com/webmachinelearning/webmcp/pull/265)

#### Human-in-the-loop & user activation

Choose a viable path and scope for user interaction.

- Elicitation [#165](https://github.com/webmachinelearning/webmcp/issues/165) and [PR #204](https://github.com/webmachinelearning/webmcp/pull/204)
- User activation [#62](https://github.com/webmachinelearning/webmcp/issues/62) and human approval bypass [#288](https://github.com/webmachinelearning/webmcp/issues/288)

### ⏸️ `12:00` (GMT) Lunch

Sussex restaurant + Bbar, Ground Floor.

### ▶️ `13:15` (GMT) Horizontal groups and coordination (joint sessions)

#### Privacy & security

>Joint with Privacy WG / Privacy IG / Security IG.

Agree concrete WebMCP mitigations, external guidance, and review follow-ups.

- Privacy mitigations [#313](https://github.com/webmachinelearning/webmcp/issues/313) and ecosystem-risk guidance [PR #334](https://github.com/webmachinelearning/webmcp/pull/334)
- Security [Threat Model for WebMCP](https://w3c.github.io/threat-model-webmcp/), related discussion [#154](https://github.com/webmachinelearning/webmcp/issues/154), prompt injection [#11](https://github.com/webmachinelearning/webmcp/issues/11)

#### WebMCP and WebExtensions

>Joint with WebExtensions CG.

Discuss integration use cases, boundaries, and next design steps.

- Separate TPAC breakout: [Integrating WebMCP into WebExtensions](https://github.com/w3c/tpac2026-breakouts/issues/84)
- Related: extension enumeration and invocation [#74](https://github.com/webmachinelearning/webmcp/issues/74), external MCP client and permissions considerations [#23](https://github.com/webmachinelearning/webmcp/issues/23)

#### Wide review follow-ups

Record remaining review requests, responses, and target dates.

- TAG [design-reviews#1238](https://github.com/w3ctag/design-reviews/issues/1238)
- Accessibility [w3c/a11y-request#189](https://github.com/w3c/a11y-request/issues/189) and related discussion [#65](https://github.com/webmachinelearning/webmcp/issues/65)
- Internationalization [w3c/i18n-request#338](https://github.com/w3c/i18n-request/issues/338)

### ▶️ `14:00` (GMT)

#### Built-in AI APIs overview

- Implementation status
- Origin/Dev Trials and [developer feedback](https://github.com/webmachinelearning/awesome-built-in-ai)
- Standards positions and wide review

#### Prompt API

> [Spec](https://webmachinelearning.github.io/prompt-api/) | [Explainer](https://github.com/webmachinelearning/prompt-api) | [Issues](https://github.com/webmachinelearning/prompt-api/issues) | [PRs](https://github.com/webmachinelearning/prompt-api/pulls)

- Model selection and availability [#169](https://github.com/webmachinelearning/prompt-api/issues/169)
- Message format for tool calling, thinking, and multimodality [#209](https://github.com/webmachinelearning/prompt-api/issues/209)
- Sampling modes [#203](https://github.com/webmachinelearning/prompt-api/issues/203), thinking effort [#222](https://github.com/webmachinelearning/prompt-api/issues/222), and `fastest` mode [#219](https://github.com/webmachinelearning/prompt-api/issues/219)

#### Writing Assistance APIs

> [Spec](https://webmachinelearning.github.io/writing-assistance-apis/) | [Explainer](https://github.com/webmachinelearning/writing-assistance-apis/) | [Issues](https://github.com/webmachinelearning/writing-assistance-apis/issues) | [PRs](https://github.com/webmachinelearning/writing-assistance-apis/pulls)

- Privacy of a paid cloud option [#84](https://github.com/webmachinelearning/writing-assistance-apis/issues/84)
- Performance preference limits and cross-API alignment [#96](https://github.com/webmachinelearning/writing-assistance-apis/issues/96) / [PR #103](https://github.com/webmachinelearning/writing-assistance-apis/pull/103)
- `contextUsage` and `contextWindow` alignment with Prompt API [#109](https://github.com/webmachinelearning/writing-assistance-apis/issues/109)

#### Translator and Language Detector APIs

> [Spec](https://webmachinelearning.github.io/translation-api/) | [Explainer](https://github.com/webmachinelearning/translation-api/) | [Issues](https://github.com/webmachinelearning/translation-api/issues) | [PRs](https://github.com/webmachinelearning/translation-api/pulls)

- Input formats for translation and language detection [#60](https://github.com/webmachinelearning/translation-api/issues/60), [#82](https://github.com/webmachinelearning/translation-api/issues/82), [#83](https://github.com/webmachinelearning/translation-api/issues/83)
- Definition of on-device models [#72](https://github.com/webmachinelearning/translation-api/issues/72)
- Batched translation [#85](https://github.com/webmachinelearning/translation-api/issues/85)

#### Proofreader API

> [Spec](https://webmachinelearning.github.io/proofreader-api/) | [Explainer](https://github.com/webmachinelearning/proofreader-api) | [Issues](https://github.com/webmachinelearning/proofreader-api/issues) | [PRs](https://github.com/webmachinelearning/proofreader-api/pulls)

- Multiple correction options [#35](https://github.com/webmachinelearning/proofreader-api/issues/35) and native spellchecker fallback [#36](https://github.com/webmachinelearning/proofreader-api/issues/36)
- HTML input [#32](https://github.com/webmachinelearning/proofreader-api/issues/32) and custom dictionaries [#20](https://github.com/webmachinelearning/proofreader-api/issues/20)

### 🌱 Proposals for new incubations

- Review and discuss any [new proposals](https://github.com/webmachinelearning/proposals) with traction:
  - Decisions API [#20](https://github.com/webmachinelearning/proposals/issues/20)
  - Semantic Embedder API [explainer](https://github.com/explainers-by-googlers/semantic-embedder-api)

### 🫶 Wrap up

- Synthesis of resolutions, next steps

### ⏹️ `15:00` (GMT) End

You may also be intested in:

### `15:30 - 16:30` (GMT)

[Breakout sessions](https://github.com/w3c/tpac2026-breakouts/)

### 🤝 `18:00` (GMT)

[Developer Meetup](https://www.w3.org/events/meetups/2026/dublin-developer-meetup/) ([registration](https://www.w3.org/wbs/1/devmeetup-dublin/))

<!--

### WebMCP issue overflow

Bring to the agenda as time allows; otherwise continue in telcons.

- Real-user measurement [#186](https://github.com/webmachinelearning/webmcp/issues/186); agent allowlist [#116](https://github.com/webmachinelearning/webmcp/issues/116)
- Concurrency [#47](https://github.com/webmachinelearning/webmcp/issues/47) / [#49](https://github.com/webmachinelearning/webmcp/issues/49), with related [PR #337](https://github.com/webmachinelearning/webmcp/pull/337)
- Defaults [#224](https://github.com/webmachinelearning/webmcp/issues/224); standardized capabilities [#168](https://github.com/webmachinelearning/webmcp/issues/168); scope boundary with remote MCP [#322](https://github.com/webmachinelearning/webmcp/issues/322)
- Frameworks [#199](https://github.com/webmachinelearning/webmcp/issues/199); progress reporting [#196](https://github.com/webmachinelearning/webmcp/issues/196)
- Multimodal tools [#41](https://github.com/webmachinelearning/webmcp/issues/41) and file attachments [#81](https://github.com/webmachinelearning/webmcp/issues/81)
- Progressive disclosure and skills [#255](https://github.com/webmachinelearning/webmcp/issues/255), [#161](https://github.com/webmachinelearning/webmcp/issues/161), [#297](https://github.com/webmachinelearning/webmcp/issues/297), [#222](https://github.com/webmachinelearning/webmcp/issues/222), [#88](https://github.com/webmachinelearning/webmcp/issues/88)
- Application-driven observation [#229](https://github.com/webmachinelearning/webmcp/issues/229) and agent sessions [#232](https://github.com/webmachinelearning/webmcp/issues/232)
- Declarative tool manifest for JS-callable tools [#341](https://github.com/webmachinelearning/webmcp/issues/341) and app-to-agent manifest [#242](https://github.com/webmachinelearning/webmcp/issues/242)
- Page-enforced write boundaries [#298](https://github.com/webmachinelearning/webmcp/issues/298) / [PR #333](https://github.com/webmachinelearning/webmcp/pull/333)
- Return the registered tool [#234](https://github.com/webmachinelearning/webmcp/issues/234) and `execute` naming [#158](https://github.com/webmachinelearning/webmcp/issues/158)
- Structured refusal signal [#282](https://github.com/webmachinelearning/webmcp/issues/282) and `sensitiveHint` [#110](https://github.com/webmachinelearning/webmcp/issues/110)
- Page-to-agent messages [#329](https://github.com/webmachinelearning/webmcp/issues/329), `toolactivated` after `execute` [#332](https://github.com/webmachinelearning/webmcp/issues/332), backend-inference use case [#343](https://github.com/webmachinelearning/webmcp/issues/343)
- Multiple elicitation requests [#50](https://github.com/webmachinelearning/webmcp/issues/50), streaming tool arguments [#82](https://github.com/webmachinelearning/webmcp/issues/82), input changed event lifecycle [#104](https://github.com/webmachinelearning/webmcp/issues/104), human-in-the-loop policy hints [#198](https://github.com/webmachinelearning/webmcp/issues/198)

### WebMCP resolved / stale / defer candidates

Confirm asynchronously.

- Close as resolved? [#133](https://github.com/webmachinelearning/webmcp/issues/133), [#10](https://github.com/webmachinelearning/webmcp/issues/10), [#191](https://github.com/webmachinelearning/webmcp/issues/191), [#30](https://github.com/webmachinelearning/webmcp/issues/30), [#85](https://github.com/webmachinelearning/webmcp/issues/85)
- Close as stale? [#39](https://github.com/webmachinelearning/webmcp/issues/39), [#38](https://github.com/webmachinelearning/webmcp/issues/38), [#28](https://github.com/webmachinelearning/webmcp/issues/28), [#25](https://github.com/webmachinelearning/webmcp/issues/25), [#166](https://github.com/webmachinelearning/webmcp/issues/166), [#256](https://github.com/webmachinelearning/webmcp/issues/256), [#97](https://github.com/webmachinelearning/webmcp/issues/97), [#103](https://github.com/webmachinelearning/webmcp/issues/103)
- Defer to backlog or other venue? [#257](https://github.com/webmachinelearning/webmcp/issues/257), [#54](https://github.com/webmachinelearning/webmcp/issues/54), [#105](https://github.com/webmachinelearning/webmcp/issues/105), [#6](https://github.com/webmachinelearning/webmcp/issues/6), [#7](https://github.com/webmachinelearning/webmcp/issues/7), [#31](https://github.com/webmachinelearning/webmcp/issues/31), [#29](https://github.com/webmachinelearning/webmcp/issues/29), [#148](https://github.com/webmachinelearning/webmcp/issues/148), [#151](https://github.com/webmachinelearning/webmcp/issues/151), [#83](https://github.com/webmachinelearning/webmcp/issues/83), [#84](https://github.com/webmachinelearning/webmcp/issues/84), [#53](https://github.com/webmachinelearning/webmcp/issues/53), [#93](https://github.com/webmachinelearning/webmcp/issues/93), [#267](https://github.com/webmachinelearning/webmcp/issues/267)

-->


</details>
