# How to scribe

## Quick start

1. Join the #webmachinelearning IRC channel: https://irc.w3.org/?channels=#webmachinelearning

2. Once the chair has assigned you as a scribe, you're all set. The scribe selection is done at the beginning of each meeting.

3. Use these key IRC commands to record the essence of the discussion:

| IRC Command	| Explanation	| Who? |
| --- | --- | --- |
| `Topic: Feature X` | Use "Topic: …" at the start of each agenda topic. This will appear in the minutes as a header. | anybody |
| `Subtopic: Feature X detail Y` | Use "Subtopic: …" for a subtopic. This will become a subheader. | anybody |
| `Mike: Feature X is great` | Record what Mike said.	| scribe |
| `... and easy to implement.`	| Mike's statement continues. Use three periods. | scribe |
| `General agreement.` | A description or summary, not attributed to a particular speaker. Only works when the scribe writes this. | scribe |

(Adapted from the [official manual](https://w3c.github.io/scribe2/scribedoc.html#notes).)


<details><summary>For advanced users only ...</summary>

# Official manuals

The official manuals for advanced users: 

- https://www.w3.org/2002/03/RRSAgent
- https://w3c.github.io/scribe2/scribedoc.html

# New features

>Based on the most excellent expert guidance by Bert Bos shared with [chairs](https://www.w3.org/mid/c34fdac7-106c-1ed4-70f9-f96a514ab0f4@w3.org).

## More than one scribe

You know you can assign a scribe:

```
scribe: Ana
```

But did you know you can also do

```
scribe+ Ana
```

Now Ana is scribe *in addition* to whoever was scribe before. Thus you can have two (or more) scribes at the same time. And when Ana stops scribing, you just do

```
scribe- Ana
```

Handy when the scribe is talking and somebody needs to fill in for a moment. Or when the speakers are talking so fast that one scribe is not enough...



## Hyperlinks

You know that you can put URLs in the minutes and they will turn into hyperlinks. Did you know that you can also hide the URL and provide
anchor text?

If you type this:

```
https://example.com/mylink
```

that URL will appear in the minutes and be clickable. But if you do this

```
-> https://example.com/mylink my link
```

the minutes will have a hyperlink with the text `my link`. Which looks much nicer. And in case you forget the syntax, all of the following also work:

```
my link -> https://example.com/mylink
https://example.com/mylink -> my link
-> my link https://example.com/mylink
```

When you need a hyperlink in the middle of a longer sentence, the easiest is that last syntax. See the manual for how to do that with the others.

## Images

You can put images in the minutes, too. It's like putting in a hyperlink, but you use a longer arrow. E.g.:

```
--> https://example.org/imgs/foo.gif it's a foo!
```

The anchor text becomes the ALT text of the image.

## Slides

If the meeting involves slides, you can embed the slides in the minutes at the right location. First, give the URL of the slides as follows:

```
slideset: https://example.com/slides/my.html
```

and then when the speaker shows slide 3, you type

```
[slide 3]
```

That `[slide 3]` will be replaced in the minutes by the actual third slide. This currently works for slides in PDF and slides in HTML using the Shower and B6+ frameworks. (These are the formats supported by a JavaScript library called i-slide: https://w3c.github.io/i-slide/)


## Verbatim text

If you want to copy-paste some literal text into the minutes without it being interpreted or reformatted, first enter a line with three backquotes or two square brackets, and also end with them, e.g.:

````
```
_:b01 fhir:active true ;
  fhir:_active [
   a fhir:Extension ;
   fhir:index 0 ;
   fhir:url "http://example.org/fhir/boolean/Certainty" ;
   fhir:valueDecimal 0.75
  ] .
```
````

or:
```
   [[
   if: a > b
     m = a;
   else:
     m = b;
   ]]
```

The colons (:) will not signify speakers, the URL will not be clickable and the spaces will stay exactly as they are entered.

## Escaped lines

A related feature is the escaped line. If you find that a line that was meant to be descriptive is interpreted as a command, put a backslash in front. E.g., if the scribe types the following line, scribe.perl will think somebody called `Result` was saying something:

```
Result: all in favor
```

But not if you type it like this:

```
\Result: all in favor
```

But you probably forgot to do that. :-) So fix it with an `s///` command instead:

```
s/Result/\Result/
```

## Subtopics

You have probably used the `topic:` command to split the minutes into sections. If you want to further split each section, there is `subtopic:`


## The scribe's personal opinion

Doing a strawpoll? And everybody says `+1`, but it shows up as

```
<John> +1
<Zoe> +1
+1
<Pol> +1
```

So who was that third vote? In fact, it was the scribe, but scribe.perl thinks the scribe was taking minutes, rather than giving his personal opinion. To fix that, the scribe can prefix his vote with his own name between angle brackets:

```
<Ana> +1
```

and scribe.perl will format this to match the style of what other people typed into IRC.

## Mathematics

Say you have just discovered that c is the square root of E divided by m, but how do you write that in the minutes? Simple: write it as LaTeX and let scribe.perl convert it to MathML:

```
$ c = \sqrt{E/m} $
```

This feature is not enabled by default. To turn it on, give this command in IRC:

```
scribeoptions: -emphasis
```

(Actually, ‘scribeoptions: -emph’ is enough.) This not only turns on math, but also some other nice formatting options, such as _underline,_ /italic,/ and *bold*.


## Pointing into the minutes

If you are linking to a specific part of the minutes, know that every line in the minutes has an ID.
</details>