## WebML WG Virtual Meeting at TPAC 2021

![WebML logo](https://raw.githubusercontent.com/webmachinelearning/webmachinelearning.github.io/main/assets/images/logo-blue.svg) ![TPAC 2021 cover](https://www.w3.org/2021/10/TPAC/images/TPAC-2021-cover.svg)

>📢 This issue is to collaboratively work out an agenda for the [Web Machine Learning WG](https://www.w3.org/groups/wg/webmachinelearning) Virtual Meeting at [TPAC 2021 event](https://www.w3.org/2021/10/TPAC/). Your suggestions for agenda topics are welcome via comments. 👇

# Registration

TPAC registration will open on 20 September 2021, register via https://www.w3.org/2021/10/TPAC/

### Logistics

CONFIRMED dates and times, 1 hour a day, subject to the agenda:

- ⏰ 26 October 2021 14:00-15:00 UTC+0 (see [your local time](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20211026T14)) - [🗓️ Calendar](https://www.w3.org/events/meetings/cfb1bec6-948f-4651-802e-f4a10c1c7ab2)
- ⏰ 27 October 2021 14:00-15:00 UTC+0 (see [your local time](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20211027T14)) - [🗓️ Calendar](https://www.w3.org/events/meetings/e70e2b4c-9313-45ec-a16e-be9746a49b80)
- ⏰ 28 October 2021 14:00-15:00 UTC+0 (see [your local time](https://www.timeanddate.com/worldclock/fixedtime.html?iso=20211028T14)) - [🗓️ Calendar](https://www.w3.org/events/meetings/9fdaa3af-5858-46c8-8ecf-05384a15636e)

* Chair: Anssi
* Scribe: ?
* IRC: irc://irc.w3.org:6667/#webmachinelearning
* IRC web client: https://irc.w3.org/?channels=#webmachinelearning
* Call-in details: https://lists.w3.org/Archives/Member/internal-webmachinelearning/2020Apr/0000.html
* Minutes:
  - https://www.w3.org/2021/10/26-webmachinelearning-minutes.html
  - https://www.w3.org/2021/10/27-webmachinelearning-minutes.html
  - https://www.w3.org/2021/10/28-webmachinelearning-minutes.html

---

### ✋ Setting the context

> TPAC meeting is an [opportunity](https://lists.w3.org/Archives/Public/public-webmachinelearning-wg/2021Aug/0000.html) for a Working or Interest Group:
>
> -  look on the progress and goals of the Group as well as the deliverables;
> -  look at related work (e.g in Community Groups) and what's new out there within the scope or related to the Group's mission;
> - welcome new participants, understand their interests, get their questions/feedback on the Group, and potentially mentor them on how to contribute;
> -  welcome observers, understand their interests in the Group, and get them interested in joining the Group and helping;

---

# Agenda

### ⏰ 26 October 2021 14:00-15:00 UTC+0 - [🗓️ Calendar](https://www.w3.org/events/meetings/cfb1bec6-948f-4651-802e-f4a10c1c7ab2) - [📝 Minutes](https://www.w3.org/2021/10/26-webmachinelearning-minutes.html)

#### ℹ️ Rationale/criteria for adding new ops to the WebNN API

Contributors: @wchao1115, @jbingham & @pyu10055, Michał Karzyński @postrational

Discuss what makes for a good criteria to ensure the WebNN API evolves and its scope is driven by right priorities, identify and distill key learnings from related work.

References:

- [WebNN use cases](https://www.w3.org/TR/webnn/#usecases) and [first-wave models](https://github.com/webmachinelearning/webnn/blob/main/op_compatibility/first_wave_models.md)
- [WebNN samples](https://webmachinelearning.github.io/webnn-samples-intro/)
- [Proposing a new op to ONNX](https://github.com/onnx/onnx/blob/master/docs/AddNewOp.md)
- [Create an op in TF](https://www.tensorflow.org/guide/create_op)
- [Writing custom ops in TF.js](https://www.tensorflow.org/js/guide/custom_ops_kernels_gradients)
- [Adding new operators, view from ONNX by Michal Karzynski](https://lists.w3.org/Archives/Public/www-archive/2021Nov/att-0000/W3C_Adding_new_Operators.pdf)

#### ℹ️ Versioning and web compatibility

Contributors: @cynthia @torgo / @w3ctag

Discuss how versioning fits into the web platform, techniques that enable conditionally running code, best practices, common pitfalls.

References:

- [ONNX versioning](https://github.com/onnx/onnx/blob/master/docs/Versioning.md)
- [Feature detection](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Feature_detection) and [Undetectables](https://github.com/Modernizr/Modernizr/wiki/Undetectables)
- [Graceful degradation versus progressive enhancement
](https://www.w3.org/wiki/Graceful_degradation_versus_progressive_enhancement)
- [New features should be detectable](https://www.w3.org/TR/design-principles/#feature-detect)

#### ℹ️ Privacy and security discussion

Contributors: Christine Runnegar @w3cping, Dzmitry Malyshau @kvark Kai Ninomiya @kainino0x Corentin Wallez @Kangz / WebGPU, @jbingham / Model Loader

Revisit privacy discussion and related work happening in the WebGPU WG, discuss fingerprinting guidance from PING and evaluate its mitigations.

References:

- [Fingerprinting Guidance](https://www.w3.org/TR/fingerprinting-guidance/) and [mitigations](https://www.w3.org/TR/fingerprinting-guidance/#mitigations)
- [WebGPU Security and Privacy Considerations](https://gpuweb.github.io/gpuweb/#security)
- [WebNN Security and Privacy Considerations](https://www.w3.org/TR/webnn/#security)
- [WebNN open privacy issues](https://github.com/webmachinelearning/webnn/labels/privacy-tracker)

---

### ⏰ 27 October 2021 14:00-15:00 UTC+0 - [🗓️ Calendar](https://www.w3.org/events/meetings/e70e2b4c-9313-45ec-a16e-be9746a49b80) - [📝 Minutes](https://www.w3.org/2021/10/27-webmachinelearning-minutes.html)

#### ℹ️ ML JS framework performance, focus areas for WebNN

Contributors: @huningxin, @wchao1115,  @pyu10055 / TF.js, @EmmaNingMS & co / ONNX Runtime Web, @dtig @penzn / Wasm SIMD, @mingqiusun / WASI

Review ML JS framework performance data across backends, discuss learnings from backend implementation efforts.

References:
- [WebNN ML JS Frameworks Performance, presentation slides](https://lists.w3.org/Archives/Public/www-archive/2021Oct/att-0014/WebNN_ML_JS_Framework_Performance.pdf)
- [ONNX Runtime Web](https://github.com/microsoft/onnxruntime/tree/master/js/web)
- [XNNPACK backend for TensorFlow Lite](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/lite/delegates/xnnpack#readme)

#### ℹ️ Integrating an open-source cross-platform implementation of the Web Neural Network API into a web engine 

Contributors: @huningxin, @fujunwei, Corentin Wallez @Kangz & co / WebGPU & Dawn

WebNN-Native is a software project that implements the WebNN API specification on top of DirectML, OpenVINO, oneDNN and XNNPACK backends across Windows 10 and Linux. In this session we will introduce the project and discuss web engine integration plans. The goal of the session is to encourage new contributors to the WebNN-Native project and identify new stakeholders interested in web engine integration.

References:

- [WebNN-native](https://github.com/webmachinelearning/webnn-native)
- [WebNN-native performance comparison](https://www.w3.org/2021/10/TPAC/demos/webnn.html)
- [WebNN implementation in Chromium Design Doc](https://docs.google.com/document/u/0/d/1KDVuz38fx3SpLVdE8FzCCqASjFfOBXcJWj124jP7ZZ4/)


#### ℹ️ Privacy and security discussion continued

Continue from where we left on Day 1. Discuss Model Loader API security.

---

### ⏰ 28 October 2021 14:00-15:00 UTC+0 - [🗓️ Calendar](https://www.w3.org/events/meetings/9fdaa3af-5858-46c8-8ecf-05384a15636e) - [📝 Minutes](https://www.w3.org/2021/10/28-webmachinelearning-minutes.html)

#### ℹ️ Conformance testing of WebNN API

Contributors: @wchao1115, @dontcallmedom, Feng Dai @BruceDai

Discuss the progress in conformance testing of the WebNN API, web-platform-tests migration.

References:
- [WebNN web-platform-tests WIP](https://brucedai.github.io/wpt/webnn/) ([tracking issue](https://github.com/webmachinelearning/webnn-polyfill/issues/2))
- [Conformance testing of ML APIs for the Web](https://github.com/w3c/machine-learning-workshop/issues/80)

#### ℹ️ Ethical issues in using Machine Learning on the Web

Contributors: @anssiko, @dontcallmedom

The Working Group is committed to develop a Working Group Note documenting ethical issues associated with using Machine Learning on the Web. Review the early document stub and have a discussion on a subset of ethical issues to focus on at the intersection of ML and the web platform.

References:

- [Ethical Web Machine Learning](https://webmachinelearning.github.io/ethical-webmachinelearning/)

### ⏰ Not yet scheduled

#### ℹ️ WebNN API spec technical discussion

The [familiar](https://github.com/webmachinelearning/meetings/tree/main/telcons) GH issue and PR-driven discussion/triage/new feature proposal review. Details to be confirmed closer to the meeting.

#### ℹ️ Technical demos

WebNN technical demos to be shared with the broader W3C community at TPAC.

As in [previous years](https://www.w3.org/2020/10/TPAC/group-updates.html#intro), as part of TPAC, W3C groups have an opportunity to produce short videos to share updates from the group's work and/or technical demos illustrating the latest developments.

Interested in sharing a demo? See [best practices](https://www.w3.org/wiki/TPAC2021/Demos_and_Group_updates#Best_Practices_for_Recording_Videos) and get in touch with @dontcallmedom (dom at w3.org).
