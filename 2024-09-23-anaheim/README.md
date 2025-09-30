<img src="https://webmachinelearning.github.io/logos/webml/logo-webml-white.png" alt="WebML logo">
<img src="https://www.w3.org/2024/09/TPAC/images/banner.svg" alt="TPAC logo">

# Registration

- Registration is now open until 13 September 2024: https://www.w3.org/register/tpac2024
- All registered WebML WG/CG participants and invited guests welcome.

# Logistics

- 🏨 **Venue**: [Hilton Anaheim](https://www.w3.org/2024/09/TPAC/venue.html) in-person & remote
- 🗓️ **Meeting invite**: [23 September 2024, 09:00–18:00 Pacific Daylight Time](https://www.w3.org/events/meetings/6c3dd4cb-e1bf-432c-92f8-fd938188a426/)
- ⏰ **Schedule**: 23 September 2024, 09:00–18:00 PDT local time (see [your local time](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20240923T1600))
  - ⏰ Start: 9:00 local / 16:00 UTC
  - ⏰ Morning break: 10:30 - 11:00 local / 17:30 - 18:00 UTC
  - ⏰ Lunch: 12:30 - 13:30 local / 19:30 - 20:30 UTC
  - ⏰ Afternoon break: 14:30 - 15:00 local / 21:30 - 22:00 UTC
  - ⏰ End: 18:00 local / 00:00 UTC
- 📞 **Zoom details**: see 🗓️ **Meeting invite** > Joining Instructions
- ✍️ **IRC**: https://irc.w3.org/?channels=#webmachinelearning or irc://irc.w3.org:6667/#webmachinelearning
- ✍️ **Minutes**:
  - https://www.w3.org/2024/09/23-webmachinelearning-minutes.html
- 💬 **Slack**: https://w3ccommunity.slack.com/#webmachinelearning ([sign-up instructions](https://www.w3.org/wiki/Slack))

### Related meetings

>[!NOTE]
>Any related meetings of interest to the WebML WG/CG participants to be listed here.

- Check out the [breakout schedule](https://www.w3.org/2024/09/TPAC/breakouts.html) for 1-hour sessions on new or existing topics

# Agenda

>[!WARNING]
>**This is a Living Agenda, please expect updates. We'll do the usual agenda bashing at the beginning of the meeting for any last-minute additions subject to available agenda time.**

## ⏰ Start meeting 9:00 local / 16:00 UTC

### 👋 Welcome

- Intros
- Agenda bashing

### 📘 Charter orientation

- WG and CG interplay
- Current scopes, future aspirations
- Deliverables: WebNN, Ethical Principles, tentative Model Loader
- Coordination with other groups

### 😇 Ethics
- `📍9:30-10:00` In-browser explainability libraries and viz tools (@xiaohk, OpenAI / Georgia Tech) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0005/jay-wang-w3c-webml-compressed-selected.pdf)

### ⏳ Spec orientation
- Triage pass through open issues: breaking changes, priorities, next steps for the issue - see [triage guidance](https://github.com/webmachinelearning/webnn/blob/main/docs/IssueTriage.md) (All)


#### ⌛ Break 10:30 local / 17:30 UTC

## ⏰ Resume meeting 11:00 local / 18:00 UTC

### ✨ New features
- A [refreshed analysis](https://github.com/webmachinelearning/webnn/issues/375#issuecomment-2292466613) of popular models, operator & data type gaps (@fdwr) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0014/WebNN_Operator_Update_Wave_3.pdf)
- Quantization and dequantization (QDQ), a bag of multiple issues (@inexorabletash)
- Platform capability detection (@philloooo) [#463](https://github.com/webmachinelearning/webnn/issues/463) [#755](https://github.com/webmachinelearning/webnn/pull/755) [opSupportLimits()](https://www.w3.org/TR/webnn/#api-mlcontext-opsupportlimits)
- Future-proof [device selection](https://github.com/webmachinelearning/webnn/labels/device%20selection) abstractions (@mwyrzykowski) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0006/MLDeviceType.pdf)

#### 🍴 Lunch 12:30 local / 19:30 UTC

## ⏰ Resume meeting 13:30 local / 20:30 UTC

### 📢 Customer feedback & collaborations
- `📍13:30-14:00` Universal Large-language Model
Deployment with ML Compilation (@tqchen) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0004/MLCTalk.pdf)
- Transformers.js WebNN backend (@xenova) - https://github.com/xenova/transformers.js/pull/890, [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0003/WebML_WG_-_Transformers.js_update__23_September_2024_.pdf)
- ONNX Runtime Web & WebNN EP
- Google Chrome Feedback revisited [#453](https://github.com/webmachinelearning/webnn/issues/453)
- Other standards positions [#763](https://github.com/webmachinelearning/webnn/issues/763)

### 🤝 Interop and cross-group coordination
- Interop issues across different backends (@huningxin)
- Core operator set [#573](https://github.com/webmachinelearning/webnn/issues/573)
- MLTensor (was MLBuffer) [#754](https://github.com/webmachinelearning/webnn/pull/754) (@a-sully) and [#760](https://github.com/webmachinelearning/webnn/pull/760) (@bbernhar)
- MLConstantOperand [#668](https://github.com/webmachinelearning/webnn/issues/668) (@reillyeon)

#### ☕ Afternoon break 16:00 - 16:30 local / 23:00 - 23:30 UTC

## ⏰ Resume WG meeting 16:30 local / 23:30 UTC

### 🔮 Implementation plans and trials

- Next step for implementations, Origin Trial or equivalent and align with framework developer feedback

### 🛤️ Advancement on the W3C Rec Track
- Wide review status, close on [TAG review feedback](https://github.com/w3ctag/design-reviews/issues/933)
- W3C “[living standards](https://sideshowbarker.github.io/w3c-faq/#living-standards)” expectations (@dontcallmedom)

### 🌱 Incubations
- Custom ops (@huningxin) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0007/Tensor_Primitive_Ops_Proposal_-_TPAC.pdf)
- Built-in APIs for [translation](https://github.com/WICG/translation-api) and [prompting](https://github.com/explainers-by-googlers/prompt-api/) (@domenic) - [slides](https://lists.w3.org/Archives/Public/www-archive/2024Sep/att-0008/TPAC_2024_Built-in_AI_APIs.pdf)
- Model management (@mmccool)

#### 🫶 Wrap up

- Synthesis of key outcomes, next steps

## ⏰ End meeting 18:00 local / 01:00 UTC

- 🍴 Group dinner
