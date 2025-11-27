<img src="https://www.w3.org/2025/11/TPAC/images/banner.svg" alt="TPAC 2025">
<img src="https://webmachinelearning.github.io/logos/webml/logo-webml-white.png" alt="Web Machine Learning">

# Working Group / Community Group F2F
## 10-11 November 2025 - 00:00-07:45 UTC / 09:00-16:45 JST

### Logistics

>- ✅ Registration: [open until 3 November 2025](https://www.w3.org/register/tpac2025)
>   - See also: [registration fee waivers](https://www.w3.org/2025/11/TPAC/registration.html#waiver)
>- 🏨 Venue: [Kobe International Conference Center](https://www.w3.org/2025/11/TPAC/#venue) ([map](https://www.w3.org/2025/11/TPAC/schedule.html#map)) in-person & remote
>   - Monday: 09:00–16:45 JST, Floor 4 - 403
>   - Tuesday: 09:45–17:30 JST, Floor 4 - 405
>   - All WebML WG/CG participants and invited guests welcome!
>- 📞 Remote joining instructions: see Invite > Joining Instructions (1 wk prior)
>- ✍️ IRC web client: [#webmachinelearning](https://irc.w3.org/?channels=#webmachinelearning)
>- 🗓️ Invites: [invite 10 November 2025](https://www.w3.org/events/meetings/f63193ec-259b-4ab8-ad65-a5a6e0adf556/), [invite 11 November 2025](https://www.w3.org/events/meetings/091a2581-034b-4afa-8ddc-91155bd4d710/)
>- ✍️ Minutes: [minutes 10 November 2025](https://www.w3.org/2025/11/09-webmachinelearning-minutes.html), [minutes 11 November 2025](https://www.w3.org/2025/11/11-webmachinelearning-minutes.html)

# Agenda

>**This is a Living Agenda. Feedback and suggestions for F2F topics welcome via comments for both `TBA` topics (To Be Announced) and timing to avoid scheduling conflicts. F2F issues are triaged as `Agenda+`.**

## 10 November 2025: 🧠 Web Neural Network API

>[!IMPORTANT]
>Meeting schedule in [Japan Standard Time (JST)](https://www.timeanddate.com/time/zones/jst). Remote participants, please note the meeting may start on 9 November in your timezone.

<details close><summary>See the timezone table ...</summary>
<table>
<tr><td> San Francisco <td> Sun, 9 November 2025 <td> 16:00
<tr><td> Boston <td> Sun, 9 November 2025 <td> 19:00
<tr><td> London <td> Mon, 10 November 2025 <td> 00:00
<tr><td> Berlin <td> Mon, 10 November 2025 <td> 01:00
<tr><td> Helsinki <td> Mon, 10 November 2025 <td> 02:00
<tr><td> Shanghai <td> Mon, 10 November 2025 <td> 08:00
<tr><td> Kobe <td> Mon, 10 November 2025 <td> 09:00
<tr><td> UTC <td> Mon, 10 November 2025 <td> 00:00 UTC
</table>

See also: [other locations](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20251110T00)
</details>

### ▶️ `09:00` (JST) Start

### 👋 Welcome

- Intros
- Agenda bashing

### 📘 Charter orientation

>[!TIP]
> Working Group [home](https://www.w3.org/groups/wg/webmachinelearning/) | [charter](https://www.w3.org/2025/03/webmachinelearning-charter.html)
>Community Group [home](https://www.w3.org/groups/cg/webmachinelearning/) | [charter](https://www.w3.org/groups/cg/webmachinelearning/)
>Web Machine Learning umbrella [site](https://webmachinelearning.github.io/) | [GH org](https://github.com/webmachinelearning)

- WG and CG interplay
- Current scopes, future aspirations
- New deliverables
- Coordination with other groups

### ⏳ Spec orientation

> [!TIP]
> WebNN API [spec](https://www.w3.org/TR/webnn/) | [explainer](https://github.com/webmachinelearning/webnn/blob/main/explainer.md) | [open issues](https://github.com/webmachinelearning/webnn/issues)

- Triage pass through open issues ([triage guidance](https://github.com/webmachinelearning/webnn/blob/main/docs/IssueTriage.md)):
  - breaking changes
  - priorities
  - next steps for the key issues
  - ...

### 💡 Case study

- WebNN Small Language Model (SLM) Performance Optimization Case Study ([slides](https://lists.w3.org/Archives/Public/www-archive/2025Nov/att-0000/WebNN_SLM_Optimization_-_TPAC.pdf)) @huningxin

### ⏸️ `10:30` (JST) Break

Drinks and snacks at Reception Hall, 3F, 4F, 5F.

### ▶️ `11:00` (JST) Resume

### ✨ New features

- webmachinelearning/webnn#573:
  - extend with attentions, MoE, TopK, MatMulNBits ... or fuse
  - performance vs. code complexity assessment results
- webmachinelearning/webnn#883: dynamic shape types
- webmachinelearning/webnn#901 @mtavenrath
- 🏷️ [Device selection](https://github.com/webmachinelearning/webnn/labels/device%20selection): seek consensus on scope
  - webmachinelearning/webnn#902
  - before graph compilation hints
    - general discussion webmachinelearning/webnn#815
    - webmachinelearning/webnn#900
  - webmachinelearning/webnn#836
  - webmachinelearning/webnn#759

### ℹ️ Proposed in issue triage

To be discussed schedule allowing:

- webmachinelearning/webnn#226
- webmachinelearning/webnn#763
- webmachinelearning/webnn#807
- webmachinelearning/webnn#6

### ⏸️ `12:30` (JST) Lunch

Lunch at Portopia Hotel, South wing, Ohwada 2/3, 1F ([map](https://www.w3.org/2025/11/TPAC/schedule.html#map2))

### ▶️ `13:30` (JST) Resume

### 📢 Customer feedback & collaborations

> [!TIP]
>See [WebNN Awesome](https://github.com/webmachinelearning/awesome-webnn) for community feedback, demos, presentations, samples, testimonials, tutorials, videos, and more. And [APIs as ladders](https://blog.sbensu.com/posts/apis-as-ladders/) essay as food for thought.

`TBA` Discuss customer feedback, including end-users, frameworks, independent software vendors.

Proposed topics:
- RTC-style workloads with response time requirements https://github.com/webmachinelearning/webnn/issues/898 @handellm / Google Meet

### 🤝 Interop and technical cross-group coordination

>[!TIP]
>WebNN [implementation report](https://wpt.fyi/results/webnn) | [wpt test suite](https://github.com/web-platform-tests/wpt/tree/master/webnn) | [webnn report](https://webnnreport.org/)

- Web Platform Tests coverage, open issues.
- `TBA` Interop issues arising from backend implementation differences that warrant WebNN spec changes.
- `TBA` Technical coordination topics with WebGPU, WebAssembly, WebRTC, other groups.

### 🚀 Implementation plans and trials

>[!TIP]
>WebNN implementation status by:
>- [Operations](https://webmachinelearning.github.io/webnn-status/#ops)
>- [Framework integrations](https://webmachinelearning.github.io/webnn-status#ops_framework)
>- Backends: [Lite RT](https://webnn.io/en/api-reference/browser-compatibility/litert), [Windows ML](https://webnn.io/en/api-reference/browser-compatibility/windowsml), [Core ML](https://webnn.io/en/api-reference/browser-compatibility/coreml)
>- [Hardware accelerators](https://webnn.io/en/api-reference/browser-compatibility/api)
>
>See also:
>- [High-level arch diagram](https://raw.githubusercontent.com/webmachinelearning/webnn/refs/heads/main/content/webnn_arch.svg)

Next step for implementations, Origin Trial or equivalent, new requirements or feedback from updates in backends, frameworks.

Kick off this session with demos that exercise diverse hardware accelerators:
  - [WebNN via ONNX Runtime Web](https://microsoft.github.io/webnn-developer-preview/):
    - Segment Anything (GPU / NPU)
    - Whisper Base (GPU / NPU)
    - Stable Diffusion Turbo (GPU / NPU)
  - [WebNN via Transformers.js](https://huggingface.co/webnn/spaces):
    - Depth Anything (GPU / NPU)
    - MODNet (GPU / NPU)
    - YOLO12n (GPU / NPU)

Possible discussion topics:
- `TBA` Browser vendors' trials
- Backends: Windows ML, LiteRT, MLDrift, Core ML
- Frameworks: ONNX Runtime Web, Transformers.js, LiteRT.js

### ⏸️ `15:00` (JST) Break

Drinks and snacks at Reception Hall, 3F, 4F, 5F.

### ▶️ `15:30` (JST) Resume

### Horizontals

Get to know experts behind horizontal groups.

#### 😇 Ethics

- [Ethical Principles for Web Machine Learning](https://www.w3.org/TR/webmachinelearning-ethics/) as a joint deliverable with the [Web & AI Interest Group](https://w3c.github.io/charter-drafts/2025/webai-ig.html) @dontcallmedom

#### 🌱 Sustainability

- [Sustainable Web Interest Group](https://www.w3.org/groups/ig/sustainableweb/) collaboration @TzviyaSiegman @mgifford
- [Web Sustainability Guidelines](https://www.w3.org/TR/web-sustainability-guidelines/) @AlexDawsonUK @mgifford
- Related: https://github.com/webmachinelearning/webnn/issues/861

#### 🔍 Privacy & Security

- Threat Modeling with Privacy and Security ([slides](https://docs.google.com/presentation/d/11m1TXLVzhnIEimyqIjgs0VTXhhA4wWIGyATEw664Ei0/)) @tjwhalen @simoneonofri

- See also:
  - 11 Nov 2025 08:30–09:30 JST [Security guidance for web developers](https://www.w3.org/events/meetings/ca0be7c4-0d4a-4d67-b815-05accd660bec/) breakout
  - 14 Nov 2025 14:00–16:00 JST [Security IG F2F](https://www.w3.org/events/meetings/bf082ff3-9b3f-4c03-9c6b-e2d30c4c99ec/) ([agenda](https://github.com/w3c/securityig/issues/30))

### 🫶 Wrap up

- Synthesis of key outcomes, next steps

### ⏹️ `16:45` (JST) End

- 🍱 Group dinner (see [1](https://www.w3.org/wiki/TPAC/2025/Restaurants) and [2](https://mgifford.github.io/Food-W3C-Kobe/))


## 11 November 2025: 🧪 Incubations: WebMCP, Built-in AI APIs

Meeting schedule in [Japan Standard Time (JST)](https://www.timeanddate.com/time/zones/jst). Remote participants, please note the meeting may start on 10 November in your timezone.

<details close><summary>See the timezone table ...</summary>
<table>
<tr><td> San Francisco <td> Mon, 10 November 2025 <td> 16:00
<tr><td> Boston <td> Mon, 10 November 2025 <td> 19:00
<tr><td> London <td> Tue, 11 November 2025 <td> 00:00
<tr><td> Berlin <td> Tue, 11 November 2025 <td> 01:00
<tr><td> Helsinki <td> Tue, 11 November 2025 <td> 02:00
<tr><td> Shanghai <td> Tue, 11 November 2025 <td> 08:00
<tr><td> Kobe <td> Tue, 11 November 2025 <td> 09:00
<tr><td> UTC <td> Tue, 11 November 2025 <td> 00:00 UTC
</table>

See also: [other locations](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20251111T00)
</details>

### ▶️ `09:45` (JST) Start

### 👋 Welcome

- Intros
- Agenda bashing

#### 🤖 WebMCP

> [!TIP]
> WebMCP [main explainer](https://github.com/webmachinelearning/webmcp/blob/main/README.md) | [API proposal](https://github.com/webmachinelearning/webmcp/blob/main/docs/proposal.md) |  [Service Workers explainer](https://github.com/webmachinelearning/webmcp/blob/main/docs/service-workers.md) | early [implementation](https://github.com/MiguelsPizza/WebMCP) [experience](https://github.com/jasonjmcghee/WebMCP)

- WebMCP intro & [demo](https://screen.studio/share/hbGudbFm) and [another demo](https://drive.google.com/file/d/1awZA2bsVNO-uUqo9NpVdnHS2Xh26Pf4u/view)
- Built-in agent ideation @huningxin
- https://github.com/webmachinelearning/webmcp/issues/35
- https://github.com/webmachinelearning/webmcp/issues/45

### ⏸️ `11:00` (JST) Break

Drinks and snacks at Reception Hall, 3F, 4F, 5F.

### ▶️ `11:30` (JST) Resume

#### 🤖 WebMCP

- https://github.com/webmachinelearning/webmcp/issues/44
- WebMCP accessibility, ARIA mapping via Declarative API: [#26](https://github.com/webmachinelearning/webmcp/pull/26) @matatk

- https://github.com/webmachinelearning/webmcp/issues/51
- https://github.com/webmachinelearning/webmcp/issues/52
- See also: other **[`Agenda+`](https://github.com/webmachinelearning/webmcp/labels/Agenda+)** issues

<details>
<summary>Other proposed topics</summary>

- To be discussed in context of [#45](https://github.com/webmachinelearning/webmcp/issues/45) <strike>Working with the [Security Interest Group](https://www.w3.org/groups/ig/security/): threat modeling [Agentic AI Web Browser](https://github.com/w3c-cg/threat-modeling/blob/main/models/agentic-ai-web-browsers.md) @simoneonofri,  [lethal trifecta](https://github.com/w3c/tpac2025-breakouts/issues/25) @johannhof</strike>
- Working with the [AI Agent Protocol Community Group](https://www.w3.org/groups/cg/agentprotocol/)
- Working with the [MCP Community](https://modelcontextprotocol.io/community/)

</details>

### ⏸️ `13:00` (JST) Lunch

Lunch at Portopia Hotel, South wing, Ohwada 2/3, 1F ([map](https://www.w3.org/2025/11/TPAC/schedule.html#map2))

### ▶️ `14:00` (JST) Resume

#### 💬 Built-in AI APIs overview

Overview, Origin Trial feedback @michaelwasserman

#### 💬 Prompt API

> [!TIP]
> Prompt API [spec](https://webmachinelearning.github.io/prompt-api/) | [explainer](https://github.com/webmachinelearning/prompt-api)

- https://github.com/w3ctag/design-reviews/issues/1093
- https://github.com/webmachinelearning/prompt-api/issues/133
- https://github.com/webmachinelearning/prompt-api/issues/159

#### ✍️ Writing Assistance APIs

> [!TIP]
> Writing Assistance APIs [spec](https://webmachinelearning.github.io/writing-assistance-apis/) | [explainer](https://github.com/webmachinelearning/writing-assistance-apis/)
- https://github.com/webmachinelearning/writing-assistance-apis/issues/83
- https://github.com/webmachinelearning/writing-assistance-apis/issues/84

### ⏸️ `16:00` (JST) Break

Drinks and snacks at Reception Hall, 3F, 4F, 5F.

### ▶️ `16:30` (JST) Resume

#### 🌍 Translator and Language Detector APIs

> [!TIP]
> Translator and Language Detector APIs [spec](https://webmachinelearning.github.io/translation-api/) | [explainer](https://github.com/webmachinelearning/translation-api/)

- `TBA` 2-3 key open issues

#### 🔎 Proofreader API

> [!TIP]
> Proofreader API [explainer](https://github.com/webmachinelearning/proofreader-api)

- `TBA` 2-3 key open issues

### 🌱 Proposals for new incubations

- Review and discuss any [new proposals](https://github.com/webmachinelearning/proposals):
  - MCP-UI

### 🫶 Wrap up

- Synthesis of key outcomes, next steps

### ⏹️ `17:30` (JST) End

- 🍣 Group dinner (see [1](https://www.w3.org/wiki/TPAC/2025/Restaurants) and [2](https://mgifford.github.io/Food-W3C-Kobe/))