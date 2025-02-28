## WebML CG Teleconference – 26 February 2025

### Agenda

[2025-02-26-cg-agenda.md](/telcons/2025-02-26-cg-agenda.md)

### Minutes

#### Participants

Etienne Noël,
Joshua Bell,
Domenic Denicola,
Mike Wasserman,
Kenji Baheux,
Reilly Grant,
Brad Triebwasser,
Rafael Cintron (Msft),
Michael McCool (Intel),
Ningxin Hu (Intel),
Yuichiro Tachibana (Tsuchiya) Dev at Hugging Face (Transformers.js),
Sushanth (Msft),
Eric Siow (Intel, AC Rep, Board of W3C)

#### Introductions

#### Summary of the current API proposals and describe status of each

https://bit.ly/tpac2024-builtinai

[Domenic provides a summary of the APIs]

Domenic: Language Detector and Translator are not powered by a LLM

... Writing Assistance APIs is using a LLM

#### Prompt API

Domenic: Not a full specs yet, but the explainer has been expanded.

... Microsoft has been working on Structured Output

... This allows you to define a JSON schema and answers you get the right schema

... This can help with standardization as you know you can get a similar format response

... Hopeful that we can use this to bring Prompt API to the web (currently only available via extensions)

... Recently added multimodal inputs in the explainer.

... All of these APIs have been going through changes across the board to align them and make them nicer.

... Used to have this availability concept.

... Now they are renamed.

... Used to give the number of bytes downloaded, now we give a progress between 0 and 1.

.... Developers can now provide expected input languages ahead of time thanks to Microsoft’s suggestions.

#### Translator

Domenic: We have the specification

... We spend some time defining edge cases, like what happens if you transfer from en to en-us, or to empty string.

Michael McCool: I’m thinking about having a tone, such as casual, or formal and you get a different translation tone.

Domenic: Good news! We have an API for that, it’s the rewriter API.

Kenji: I’m aware of one piece of feedback where one developer wanted control over formal or not.

Domenic: Let’s consider filing an issue for this

Sushanth: One topic ahead was, how would you give users the identification that this is machine translated? I think the model isn’t giving confidence. Should we be able to tell users about this?

... Second topic, among the errors, I had a bug around profanity filtering. Should one of the errors be output filtered? Should we add a response redacted error?

Etienne: Why does the browser need to know this? Wouldn’t that be the developer signaling this to users?

Sushanth: I think the browser agent would want to know but I’m also wondering what your thoughts are.

Domenic: It’s something we have been thinking about.

... Separately, returning a confidence score to the translation is really interesting.

Michael: Getting a score might require more computation.

Domenic: For your second question, I don’t know how regressive our filter is for translation but we do have something for Prompt.

... Next thing we will be working on in the spec, is the permission. We want to make it clearer.

Kenji: As long as the input and output are in sync, there are less issues. But, if the model injects unexpected things, that might be a bit more risky. For translation, since it doesn’t use an LLM, it might tend to hallucinate less.

#### Writing Assistance APIs

Domenic: We have the specification

[Domenic going through the specifications.]

Domenic: For options, there is some normative guidance that we are trying to define.

... We are reasonably happy for the Summarizer API.

... Rewriter and Writer not specified yet but will be very similar.

Michael: One thing I’ve seen is what type of content you have. Summarizing a meeting is different then summarizing a presentation.

Domenic: Ideally, it’s not necessarily something developers have to provide but it is a good point.

... We have been getting a lot of good feedback, Kenji will touch base on this a bit.

... We have received feedback that the `ai.*` pattern is problematic. `ai` is so short that sometimes the minimizer uses it and can cause conflicts. W3C and Apple have said that `ai` is too specific since we might eventually not use AI for these features in the future. We will move to something like: `Translator.create()` and do a big renaming across APIs.

... Wanted to give this group a heads up and ask feedback from the group.

Reilly: Have we objected to the navigator.ml namespace?

Domenic: We haven’t thought about that.

Reilly: Creating a global function could be worth considering: navigator.ml.createTranslator

Kenji: I can share the OT feedback

... Our origin trials (translator, prompt and summarizer) are 5X what we typically see versus average of OTs

... It’s in the top bucket of usage

... It’s going well and there’s a wide range of interest from small to large partners, e-commerce, travel, etc.

... We have run a survey for a couple of weeks to ask for feedback.

... About design, usability, quality, stability and overall satisfaction

| API                  | Stats   | Design & usability | Quality of the output | Stability | Performance | Satisfaction |
|----------------------|---------|--------------------|-----------------------|-----------|-------------|--------------|
| Summarizer           | Average | 7.8                | 7.6                   | 7.2       | 7.7         | 7.8          |
|                      | Median  | 8.0                | 8.0                   | 8.0       | 8.0         | 8.0          |
| Language Detector    | Average | 8.5                | 8.5                   | 8.4       | 8.4         | 8.8          |
|                      | Median  | 9.0                | 9.0                   | 9.0       | 9.0         | 10.0         |
| Translator           | Average | 7.9                | 7.6                   | 7.5       | 7.5         | 8.0          |
|                      | Median  | 8.5                | 8.0                   | 8.0       | 8.0         | 9.0          |
| Prompt for extensions| Average | 8.2                | 8.2                   | 7.5       | 7.2         | 8.1          |
|                      | Median  | 8.0                | 8.0                   | 7.5       | 8.0         | 8.0          |

... 0 is a disaster, 10 is perfect, don't change anything.

... Score is pretty high for design & usability and quality

... For stability we have some work that we need to do.

... Performance and satisfaction are somewhat important.

... The number of responses is not thousands but it’s a good chunk of people that have taken the time to fill out the survey.

... There is also qualitative feedback that we will filter and share what we can

#### Roundtable with all the browser vendors

Mozilla’s Firefox AI Runtime?

Sushanth: What they have created is named model that can be shared across origins.

Michael: I’ve pointed issues with Cache attacks and fingerprinting. You could potentially do timing checks and what not.

Domenic: It’s only available through extensions

... They take a task based approach and it’s a very interesting 

Sushanth: Contrasting these two, Firefox will get more flexibility. Have you seen from OT the desire from developers to customize models

Kenji: We are getting feedback to get LoRA support. Problem is providing LoRA support without making it cumbersome for developers to support when models are updated.

... Also, browsers will have a hard time to make it safe if you bring your own LoRA.

... What is interesting about the Firefox approach, is relying on describing the task versus relying too much on the model version. This makes it easier to share models across origins.

... I like this idea of leaning into tell me what you want and we will find the right model.

Natasha: Have you been asked to support an open source model for the Prompt API

Kenji: We are interested in exploring the ability to plug in custom models

... We want to understand the use cases and constraints.

... Interested in getting in touch with developers that are interested in sharing models across origins. It will be hard to agree on sharing one specific model for all the use cases. The Firefox approach might work better for caching.

Michael: We can do both in theory.

... Task-specific is fine since that’s what all the other APIs are doing anyway.

Sushanth: Sharing models across origins is great for download but if you want to have two tabs wanting to summarize, this means you might have two copies in the GPU memory.

Michael: This might be an implementation detail

Rafael: Tarek (Firefox) gave a presentation and I provided feedback.

... In his approach, he let you be very specific with the model, like I want this XYZ model from Hugging Face. He chose the ONNX runtime but not everyone might be using it. If we do agree, then we need to agree on the ops, which is what we are trying to solve on WebNN.

Kenji: To add to that, there’s also the ability to know if the device can run the model before downloading it. Being able to do a benchmark ahead of time might be useful.

... What interests or doesn’t interest you about the APIs?

... For the latter, we would like to understand concerns, reservations and what could make you change your mind?

Etienne: What is the general sentiment about the built-in AI APIs that Chrome is proposing.

Sushanth: We are focused on hearing what our developers want.

... Interop concerns with the Prompt API (maybe structured output can solve this)

... We will be trying to prototype some of this.

Michael: Can I use the Prompt API in a service worker, in WinterCG?

... Where can I use it?

Domenic: On the extensions now

... If we can figure out standardization, maybe we can bring it to the web.

... We don’t have a specification yet, but we should have something eventually.

Ningxin: Have we received feedback from developers that they want to provide execution hints. In WebNN, we have a power preference (like low power, etc). If a developer cares about power performance 

Kenji: We have a few developers that have requested better ways of controlling how/when to do AI tasks. However, it’s a very low amount of feedback.

... We should keep an eye open to that but it will be a matter of prioritization. Eventually we want to target NPU

Ningxin: If users want to bring their own model and have it work with the built-in AI apis. 

Kenji: There are some signs that certain partners have custom models they want to use for students or employees. 

... Not clear if they want to use their own framework or switching the model for built-in AI APIs. Working on clarifying use cases and the needs.

#### Process discussion

Etienne: I want to provide you with the ability to suggest topics. I propose that we open a Github issue for each future iterations of this meeting:

https://github.com/webmachinelearning/meetings/issues/31 
