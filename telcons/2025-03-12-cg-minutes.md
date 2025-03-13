## WebML CG Teleconference – 12 March 2025

### Agenda

[2025-03-12-cg-agenda.md](/telcons/2025-03-12-cg-agenda.md)


### Minutes


#### Participants

Etienne Noël,
Michael McCool,
Joshua Bell,
Domenic Denicola,
Rafael Cintron,
Natasha Gaitonde,
Sushanth Rajasankar


#### OT Feedback from partners

Etienne: Sorry to postpone again, since we have mentioned to partners that we are engaging in standardization, we have some partners that are now interested in becoming public so we are working with them on getting their names out.


#### Proofreader API

Etienne: Feedback welcome!

Michael: Will this propose new change or styles?

Domenic: Use case is similar to what a traditional word processor would spit out

... Nowadays, word processors are more powerful and can adapt the style

Michael: You would need to define the style you want

Domenic: You might view error corrections along the styles

Josh: Can you integrate it easily with squiggly lines

... Having a demo that we can play along with content editable

Michael: Can you share a demo?


#### Prompt API

Etienne: Appetite to standardize Prompt API and make it available on the Open Web?

Michael: Generally the web stays away of conformance testing.

... But if you had a set of problems and what you expected the output to look like for a certain input.

... There aren’t that many browser vendors and I believe that developers can figure it out.

Domenic: Pretty scared of anything that relies on developers testing. There are a lot more browser vendors than engine vendors and this is an area 

Michael: How many models would there be? Is it changing often? Is it per platform?

Rafael: Would like the structured output play out before we open the floodgates. We see that the output can be very different.

Domenic: There is a danger that they won’t use it

Sushanth: We need more data as what we have experimented is very finicky. Even amongst the same browser with different models. Making it available to the Open web would make it hard for compat reasons.

Michael: Developers are used to LLMs not being 100% reliable and so will they structure their application to account for that.

Etienne: If we had a way for developers to know exactly which model they would be targeting, do we feel this is such an important use case that we should ship it and make it available?

Sushanth: Maybe a list of common use cases that we can test for

Domenic: Test suites are pretty good.

... You don’t necessary want to constraint the model’s creativity.

... Right now, developers can figure it out at runtime by testing the API using a series of prompt and see how it responds.

... We could put in the API, an input output pairs, similar to some test 

Rafael: I think it will come down to what we see the use cases will be.

... Maybe users have a bad experience and they don’t know that the Prompt API is behind this.

Michael: Ways to improve the situation:

... Testing

... Like the idea of runtime testing

... What if we had some standardized finetuning data

... Something like a template and testing the models.

Natasha: Without the structured outputs, it feels early. Without some guarantees of compat, this feels a little risky.

Sushant: There are some examples where runtime testing would not work in Phi4, in a game for example.

... Another example system prompt where you say I want you to speak in old english and if you repeat the same questions twice, it breaks out of characters.

Etienne: Use cases

... Receipt OCR

... It seems like if we have a clear plan of next steps and requirements before re-evaluating.

... Need clear use cases

... Need structured outputs

... Anything that we are not thinking about or is anyone really opposed to shipping this? Want to make sure that my excitement with this API doesn’t cause us to have tunnel vision.


#### Recent spec changes and discussions recap

Domenic: Token accounting API renaming options

-> https://github.com/webmachinelearning/writing-assistance-apis/issues/5#issuecomment-2683970259

Domenic: Other changes, namespace changes

... Instead of `ai.summarizer` it’s `Summarizer`

... We are working on permissions policy and not allowing it on third-party policies

... We are removing service worker supports for this for now until we get clear use cases

Michael: On quota, can you put a lower bound quota?

... Let’s say you have a 4000 context window. Can you say you at least get 4000 characters.

Domenic You cannot.

... Example, you inject a prompt or control character.

... If you had a characterization scheme of 1 token per character, then 

Michael: I would like to see WebNN working inside Web Workers. I think there are use cases where I want to see these things working inside workers.

... I can also see places where I want to do stuff in the background async.

Domenic: Dedicated workers can be tied to a parent worker.

... Shared and service worker is much harder.

Sushanth: Had a question for summarize and proofreader API. Who’s responsibility is it to chunking the text?

Domenic: Ideally it would be the user agent. In practice, there are limits and they might have to do it themselves. For now, we haven’t done it in Chrome.

Sushanth: We have an API for what the max size is?

Domenic: And a measure to check what it would be.

Michael: Talking about characters and tokens. Is there any way that I can put the raw token output and feed it back into the LLM.

Domenic: For the Prompt API, we have created the session concept so it stays into.

... For the other APIs, we have nothing to say just change the last sentence.

Michael: Is there a case where we want to manipulate tokens directly?

Sushanth: Compat issues

Domenic: Some have expressed the desire to get logprobs.

Sushanth: For the proofreading API, any way to cache and be more performant like when a sentence is  being rewritten?

Etienne: It’s a really good question, can you open an issue so we can discuss this?

Michael: I’m seeing extensions that are doing cross-origin caching. So if they are getting tricked, maybe we should do it right.
