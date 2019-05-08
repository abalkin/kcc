# k crash course
*not safe for work,
not for the faint of heart*

<me@kel.as>

## who is k

`k` is basically Arthur Whitney, the principial designer of a computer language
called `k`, who is an iconic figure in an elite, tight-knit global community
of some of the sharpest and sophisticated programmers working for some of the most
influential institutions on the planet. Since early 90's, he provides them with 
consistently ever more powerful revisions of one single product he has been working on
his entire life, a unique integrated platform for creating very high performance applications
that deal with very large amounts of data. And they like and appreciate Arthur at least as 
much as his product.

There is a very high chance that you heard the legend of Arthur Whitney and his language; 
a **lot** of people do; what is less likely is that you have ever met 
someone who told you he or she is a professional k programmer, not just because there are rare,
but because in their lines of work is often stated in their contracts what they can and 
cannot talk about, and `k` language doesn't really need any extra publicity anyway.

What is much easier to hear is about implementations of similar systems in languages
such as C++ or Java that involve thousands of lines of code written by large teams 
and built on top of complex library stacks and even more complex infrastructure. What 
these guys are not allowed to tell tou is that the projects they are working on are 
way over budget, totally past deadline and implementing an an utterly outdated spec.

In comparision, a typical k solution is at least several factors of magninude less code, 
usually implemented by a small team or even a single individual, rarely requires 
external dependencies and is usually *complete on time*. The platform is not free
and is not not cheap, but the k paradigm enables unprecedented efficiency and ease of 
prototyping, development, testing, deployment and support of highly efficient and robust 
systems that quickly return the investment.

## what is k

`k` is a very remarkable piece of software. Formally, it is an interpreter of a 
computer language, and then some more.

The power is in the language itself which is designed from ground up primarily as 
a *tool of thought*. The vocabulary, syntax and the choice of abstractions 
offered by the language all work together to foster and propel creative, focused 
and succinct thinking about a problem and quickly finding an efficient and elegant 
solution for it. Contrary to the majority of other programming workflows, a k 
programmer spends most of his time on thinking about the problem rather than typing 
and navigating the source code tree. The actual attack on the problem is performed 
exclusively via REPL. Rapid interactive prototyping driven by agile and fluent thought 
process which is only interrupted by as few keystrokes as possible is the essence of the 
programming experience in k — an experience that each and every k programmer 
considers immensely rewarding and aesthaetically satisfying.

In addition to being an excellent tool of thought, k is also an astonishingly 
efficient computer language. The entire system, a tiny binary executable only
100 kilobytes in size without a single external dependency that fits comfortably in 
the cache of a commodity CPU, implements fundamental algorighms, data structures, 
techniques and computational primitives that withstood the test of many decades 
of production use in some of the world's most demanding data processing environments. 
The inner components of the system are polished to fit together and complement each 
other to deliver performance which many outsiders find very difficult to believe 
at first. It is also not uncommon for k newcomers to experience total shock when 
they first realize what kind of power they can wield with just a few precise
keystrokes.

This crash course is not looking to make you an expert k programmer, because
that takes years. We heard that one can teach oneself Java in 24 hours, but we 
do not feel qualified to talk about that. We are going to talk about `k`, and the
the curve will be steep, but we value your time, so it will be brutal.

## price of k

If you **have** to ask, you can't afford it. If you know **how** to ask, you will get it 
for free and for life.

## where is k

A trial version of `k` with a draconian limit of 1 gigabyte addressable workspace is 
distributed for free via Anaconda in form of x64 builds for Linux and macOS. If you 
are on Solaris, z/OS, ARM, don't worry, good things come to those who wait.
If you are on Windows, lets not cry over spilled Guinness.

Go to https://anaconda.org/ and follow the instructions. Anaconda shell integration 
option is recommended. Once you install Anaconda, install shaktidb, which is `k` in 
disguise:

`$ conda install -c shaktidb shakti`

New builds are usually published several times a week, so make sure to always 
use the latest version:

`$ conda update -c shaktidb shakti`

## starting k

Assiming conda's `bin` is in you PATH, start a `k` session like so:

```
kelas@failbowl ~ $ k
2019-04-21 15:38:18 40core 512gb avx2 © shakti m2.0 prod
 2+2
4
```

At any time during `k` session, you can:

`\h` quick reference (seriously NSFW)

`\l` changelog

`\\` bail


## style of k

**Annotations** in your `k` code is the best way not to end up coding Java for food, unless 
you are Arthur Whitney. We dare to assume you are not quite there yet, so comments start 
with `/`. When used inline, prepend a space:

```
/line comment
42

42 /inline comment
```

**Identation** in `k` is a painful subject. Basically, what you want is *no identation*.
This means if your function body is getting so much larger than life that you are tempted to split it
into lines, you either need to refactor, or your entire train of thought got derailed and you 
need to go back to the blackboard. Sometimes, however, identation is ok,
and it is **always one space**. Tabs will be frowned upon, because they will end up taking up
other people's precious screen real estate, and humans generally get really itchy when it comes 
to brick and mortar.

**Capitals**, by convention, are used by `k` programmers very sparingly, normally as a last resort 
measure. This applies both to code and comments. Identifiers in CamelCase is considered bad 
form but sometimes tolerated, and `c_style` is not permitted at all since underscore is an 
operator. Function and variable identifiers are very often boiled down to 
an absolute minumum, short identifiers 1-3 chars long are commonplace, which does not impact 
readability and comprehension given that definitions are adequately annotated. Short 
identifiers might sound like a bad idea to a Java programmer not used to identifiers shorter
than 100 bytes, but a well-structured and well-formatted k program typically fits on 
a single screen and requires little or no scrolling, and jumping between source 
files is more of an exception than a rule. The way our brain works is when the 
entire program fits into your visual buffer, "cryptic" identifiers are no longer a 
problem, because their annotated declarations are also right in front of you:

```
kei:42 / kenneth eugene iverson
```

**Function** is a first-class citizen, we have lambdas, evals and applys, everything is 
all there. It takes a man to believe it, but `k` is actually more lispy than certain Lisps,
only you don't need to get past any parens. `car` is not quite there because there are 
no *linked lists*, because `k` is designed to be *fast*.

**Implict arguments** is an empitome of brevity and wit. All functions in `k`, unless 
stated otherwise, have up to three implict arguments, `x`, `y` and `z` respectively.
Here are your first functions:

```
 f:{x+y+z}    /declaration
 f[1;2;3]     /call
6             /result
  
 f:{x*x}      /redeclaration
 f 2          /one arg, ok to omit brackets
5             /gotcha
```


**Assignment** operatior, as you have correctly guessed, is a *colon*. This fact
has a lot to do with k heritage, which is best elucidated by a simple, yet profound
thought experiment. Consider the following line of code:

```
x = x + 1
```

Although the meaning of this expression is intuitively clear to any programmer, any
mathematician will instantly respond with a succinct **"no, it is not"**. This gives
and excellent hint about how to approach the rest of this document: pretend you never
wrote a program in your life before, which is a simple trick to overcome the feeling 
that someone is trying to make you adopt a totally new way of thinking. Make no mistake, 
this is what this document is all about, but you know you want to give it a try.


## actual crash into k

**Disclaimer** is to inform you that nowhere above you were promised a gentle 
introduction. You have been warned. From here on, you are on your own with your intelligence and grit.

Without giving you anything else about how k works, we are going to contemplate a toy k implementation of a СAR Hoare's `qsort`, which you definitely remember from you freshman year, and those 20 pages of pseudocode from CLRS that you hated so much. Let's dive in:





