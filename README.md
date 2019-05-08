# k crash course
kelas <me@kel.as>

## who is k

Arthur Whitney, the principial designer and architect of a computer language
called `k`, has become a central figure of an elite, tight-knit global community
of highly skilled programmers. Since early 90's, he provides them with new revisions of one 
single product, a unique integrated platform for creating high performance 
applications for financial and other data-intensive applications. It is very 
remarkable piece of software.

There is a very high chance that you heard something about the legend of Arthur Whitney
and his language; what is less likely is that you have ever met someone who told 
you he or she is a professional k programmer, because in their lines of work is often 
stated in their contracts what they can and cannot talk about, and `k` language
doesn't really need any extra publicity anyway.

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

The power is in the language itself which is designed from ground up primarily as 
a *tool of thought*. The vocabulary, syntax and the choice of abstractions 
offered by the language all work together to foster and propel creative, focused 
and succinct thinking about a problem at hand and finding an efficient and elegant 
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

```kelas@failbowl ~ $ k
2019-04-21 15:38:18 40core 512gb avx2 © shakti m2.0 prod
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
This means if your function body is getting so larger than life that you are tempted to split it
into lines, you either need to refactor, or your entire train of thought doesn't hold any 
water at all and you need to go back to the blackboard. Sometimes, however, identation is ok,
and it is *always* one space. Tabs will be frowned upon, because they will end up taking up
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
  6          /result
  
f:{x*x}      /redeclaration
f 2          /one arg, ok to omit brackets
  5          /gotcha
```


**Assignment** operatior, as you have correctly guessed, a *colon*. This fact
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





















## Section 1: Array Power

1. Much of the expressiveness of k derives from the fact that most operations 
that operate on atoms (scalars) generalize nicely to arrays (vectors).

Examples:

```
 2*2
4
```

```
 1 2 3 4 * 3 8 10 8
3 16 30 32
```

 1 2 3 4 * 10
10 20 30 40

2) Moreover, there are nice ways to generate arrays either deterministically
or randomly.

Examples:

 x: !10
 x / this is the enumeration of 0 1 2 3 4 5 6 7 8 9 (but summarized):
!10

  5 + x
5 6 7 8 9 10 11 12 13 14

 / because of randomness, your result might not exactly match the above
 10 ? 50 / generate randomly with replacement (so there can be duplicates)
24 45 39 49 30 18 18 0 42 35

 10 ? 10
5 3 8 1 6 6 5 6 7 6

 -10 ? 10 / generate randomly without replacement (no duplicates)
3 0 7 1 8 5 9 6 4 2


3) There are more advanced ways to generate random arrays:

/ recall uniform random with replacement 
20 ? 100 

17 41 34 97 33 83 20 58 50 74 7 53 52 37 63 12 80 90 52 21


/ uniform random with replacement between 0 and 1
? 20 
0.4697213 0.785009 0.5580712 0.9615994 0.1120246 0.6466671 0.2255046 0.1409736 0.3089171 0.4539798 0.3739309 0.1362654 0.3392962 0.06063999 0.5963119 0.6279038 0.2538702 0.510196 0.7872552 0.6983393

/ Others are on the way. (To be added)


4) There are ways to reduce arrays to single values.

Examples (because of the use of randomness, your results may not be
the same as those you see here):


 y: 21 ? 300 / generate randomly with replacement
y 
151 99 244 50 193 209 167 191 221 197 178 293 38 234 163 104 255 201 80 49 180

 
 |/y / maximum
293
 
 &/y / minimum
38
 
 #y / count of elements
21

 (+/y)%(#y) / average (arithmetic mean)
166.5238


5) There are ways to index arrays.

Examples:

z: 22 + !10
z
22 23 24 25 26 27 28 29 30 31

 z[0]
22

 z[3]
25

 z[3 5]
25 27

 z[2+!6]
24 25 26 27 28 29
 
 z[(#z)-1]
31
 
 z[_ (#z) % 2]
27

6) Now consider multi-dimensional arrays.
 
 mymulti: (1 2 3; 4 5 6; 7 8 9; 10 11 12)
 mymulti
(1 2 3;4 5 6;7 8 9;10 11 12)

/ we interpret mymulti as a four row three column matrix

 mymulti[0;0]
1

 mymulti[2;0]
7

 mymulti[1;2]
6

/ Now we can get full rows

 mymulti[1]
4 5 6

/ and full columns

 mymulti[;1]
2 5 8 11


Section 2: Verbs, Adverbs, and User-defined Functions


1) The operations in k7 are called 'verbs' and often have 
two meanings depending on whether they are 'unary' (applied
to a single argument)
or 'binary' (applied to a pair of arguments).
Normally, the binary verb  will be the more familiar one.
Much of the power comes from applying the verbs to arrays.

Examples:

unary + (flip or transpose)

 x: (1 2 3 4; 5 6 7 8) / assign to x  a two row array whose first row is 1 2 3 4
  +x
(1 5;2 6;3 7;4 8) / a four row array (transpose of x) whose first row is 1 5

binary + (plus)

2 + 3 / scalar (single element) addition
5

 x + x / array addition
(2 4 6 8;10 12 14 16)

 2 + x / element to array addition


2) Just as most human languages have verb modifiers called adverbs,
k7 does too. They apply to most unary and binary operators.
Thus, the / adverb (called 'over'), besides indicating a comment, 
also causes the binary version of the verb to apply to the elements
in the array in sequence and yields a single result.
The \ adverb (called 'scan') does the same but keeps all the intermediate
results.


Examples:

 +/ 1 2 3 4  / Apply the + operator between every pair of elements; produce sum
10

  +\ 1 2 3 4 / Same as above but produce all partial sums
1 3 6 10

3) Adverbs can modify verbs directly
but can also modify verb-adverb combinations (which
are lifted to verb status). The ' (each) adverb takes both roles.



 x
(1 2 3 4;5 6 7 8)

  +/'x / Apply +/ to each row of x
10 26

 +\'x / Apply +\ to each row of y
(1 3 6 10;5 11 18 26)

4) Adverbs can modify user-defined functions as well.

  f:{[a] (a*a)+3 }
 f[4] 
19

Now we can apply f to each element of an array using the each adverb.

 f'1 2 3 4
4 7 12 19

6) While verbs combined with \ and / have the syntactic form of unary verbs,
verbs combined with \: and /: have the syntactic form of binary verbs.
Examples:

There is \: (each left):

 1 2 3 4 +\: 10
11 12 13 14

There is each right:

 20 +/: 1 2 3 4
21 22 23 24


8) There is each left each right (which should be interpreted
as performing an each left on successive elements of the right array):

 1 2 3 4 +\:/: 10 20 30 40 50
(11 12 13 14;21 22 23 24;31 32 33 34;41 42 43 44;51 52 53 54)

Eachright eachleft considers each element of the left array one at a time 
and applies
+/: to the that element and the right array

  1 2 3 4 +/:\: 10 20 30 40 50
(11 21 31 41 51;12 22 32 42 52;13 23 33 43 53;14 24 34 44 54)


9) This also applies to binary verbs.
Examples:

g:{[a;b] a + (7 * b)} 

g[2;3]
23

Eachleft considers each element of the left array one at a time and applies
g to that element and to the entire right array.

1 2 3 4 g\: 10 20 
(71 141;72 142;73 143;74 144)

Eachright considers each element of the right array one at a time and applies
g to the left array and that element. 

1 2 3 4 g/: 10 20
  (71 72 73 74;141 142 143 144)

Eachleft eachright considers each element of the right array one at a time 
and applies
g\: to the left array and that element. 

1 2 3 4 g\:/: 10 20
  (71 72 73 74;141 142 143 144)

(Try for example 1 2 3 4 g\: 20)

Eachright eachleft considers each element of the left array one at a time 
and applies
g/: to the that element and the right array

1 2 3 4 g/:\: 10 20
  (71 141;72 142;73 143;74 144)

(Try for example 3 g/: 10 20)

Finally, each can apply to just one argument

 x1: 1 2 3 4
 x2: 50

 g[;x2]'x1
351 352 353 354

 g[x1]'x2
351 352 353 354

10) Extended Example: matrix multiplication

Recall that matrix multiplication involves the dot products between rows of the left
matrix and the columns of the right matrix.

Example:

 leftmat: (1 2 3; 4 5 6; 7 8 9; 10 11 12)
 leftmat
(1 2 3;4 5 6;7 8 9;10 11 12)


 rightmat: (100 200 300 400 500; 1000 2000 3000 4000 5000; 10000 20000 30000 40000 50000)
 rightmat
(100 200 300 400 500;1000 2000 3000 4000 5000;10000 20000 30000 40000 50000)

 dot:{[v1;v2] +/ v1 * v2} / dot product function

   dot[4 5 6; 300 3000 30000]
196200


matmult:{[m1;m2] m1 dot/:\: +m2}
matmult[leftmat; rightmat]

(32100 64200 96300 128400 160500;65400 130800 196200 261600 327000;98700 197400 296100 394800 493500;132000 264000 396000 528000 660000)

11) Adverbs Replace Loops.

K programmers tend not to need loops. In fact, some of them disdain loops.
The reason is simply that the language uses adverbs instead of loops.

For example, the loop

result = 0
for i = 1 to len(myarray)
  if f(myarray[i]) then result += 1

becomes
result: +/f'array

In principle each invocation of f could (and will eventually) be done 
in parallel.

By contrast, the loop

result = 0
for i = 1 to len(myarray)
  if result = f(result, myarray[i])

becomes / or \ at least for some f's

Example:
 myarray: 2 2 2 2
 f:{[x;y] x + 2*y}

 f\ myarray
2 6 10 14

 f/ myarray
14

Second example where k's initializations can be useful:
 g: {[x;y] x*y}
 g\myarray
2 4 8 16






  


Section 3: Other Basic Verbs

Until now, we have touched on only a few of the verbs and types.
Here is Arthur Whitney's full list. We'll go over them in turn.
From what you understand already, these won't be hard to learn.


Verb        (unary)   
: gets                
+ plus       flip     
- minus      negate   
* times      first    
% divide     sqrt     
! mod|div    enum    
& min|and    where                         
| max|or     reverse  
< less       asc     
> more       dsc    
= equal      group 
~ match      not
, concat     enlist                        
^ except     null                          
# take|shape count                        
_ drop|cut   floor                       
$ cast|+/*   string   
? rand|find  unique  
@ at         type   
. dot        value 

First, let's look at how to read this table.
In each row, the binary meaning precedes the unary meaning.

Let's go in turn.

0)
/ this is a comment
\\ if alone on a line exits the k7 session or a debugging environment


1) : gets                

/ gets indicates assignment
 x: 1 2 3 4
x 
1 2 3 4

2) + plus       flip     

 2 + 3
5

/ Unary + (transpose)

 + (1 2 3 4; 5 6 7 8)
(1 5;2 6;3 7;4 8)

3) - minus      negate   

 2 - 3
-1

/ Unary - (negation)

 - 3 4 5
-3 -4 -5

4) * times      first    

 4*5
20

/ Unary * (first in list)

 * 15 24 19 10
15

5) % divide     sqrt     

 5 % 3
1.666667

/ Unary $ (square root)

 % 81
9f

6) ! mod|div    enum    

 14 ! 3
3

/ Unary ! enumerate either by integer or fload

 !20
!20


7) & min|and    where                         

 5 & 3
3

 1 & 1
1

 1 & 0
0

/ Unary & (indexes where a there is a non-zero)

x: 4 8 9 2 9 8 4

x = 9 / 1 will indicate a match
0 0 1 0 1 0 0


 & x = 9 / locations in the list above that are 1
2 4


 x > 4
0 1 1 0 1 1 0

 & x > 4
1 2 4 5



8) | max|or     reverse  

  5 | 3
5
 1 | 0
1

/ Unary | reverses lists

 | 2 3 4 5 6
6 5 4 3 2

9) < less       asc     

 5 < 3 / returns 0 because false
0
 3 < 5 / returns 1 because treu
1

/ Unary < says which order of indices gives data in ascending order

 x: 6 2 4 1 10 4
xind: < x / index locations from smallest value to highest
  xind
3 1 2 5 0 4
/ Notice that x[3] is 1, the lowest value in the list


 x[xind] / sort the values in ascending order
1 2 4 4 6 10

10) > more       dsc    

 5 > 3
1
 3 > 5
0
 x: 6 2 4 1 10 4

/ Unary > says which order of indices gives data in descending order

 xind: > x / index locations from highest value to smallest
 xind
4 0 2 5 1 3
 x[xind] / descending sorted order
10 6 4 4 2 1


11) = equal      group 

 5 = 5
1

 1 2 13 10 = 1 2 13 10 / element by element
1 1 1 1

 1 2 14 10 = 1 2 13 10 / 0 at position 2 indicates inequality
1 1 0 1


/ Unary = gives a dictionary mapping values to indexes where 
/ values are present

  = 30 20 50 60 30 50 20 20
30 20 50 60!(0 4;1 6 7;2 5;,3)

/ In the above example 20 is at positions 1 6 and 7
  x: = 30 20 50 60 30 50 20 20
x[20]  / index by the value and get the locations


12) ~ match      not

 1 2 13 10 ~ 1 2 13 10 / should match
1
 
 1 2 10 13 ~ 1 2 13 10 / does not match (order matters)
0

/ Unary ~ (like the Boolean not operator except that any non-zero becomes zero)

 ~ 1
0
 ~ 0
1
 ~ 5
0
 ~ -5
0



13) , concat     enlist                        

 x: 10 11 12 13

y: 4 3

x,y / concatenate one way    
10 11 12 13 4 3

 y,x / concatenate the other
4 3 10 11 12 13

 z: y,x
z[4] / can index these as if these were an array
 12
 
 z[2+!3] / can fetch many indexes
10 11 12

/ Unary , converts a scalar (atom) into a list or a list into a deeper list

 x: 5
x / x is an atom 
5
 *x / first on an atom is just the atom itself
5

 x: ,5 / x is now a list
 
 x / Note the comma in front indicating that x is  list
,5

 y: x,15
y / the comma goes away since atoms always have a single element 
5 15

 *y / The * operator takes the first element of a list
5

 *x  / The * operator takes the first element of a list even a singleton
5


14) ^ except     null                          

 x: 8 7 6 5 2
y: 2 5 3 7

x ^ y / elements of x (preseving order in x) that are not in y   
8 6

 y ^ x
,3


/ Unary ^ tests whether the argument is null
/ I don't really know why this is useful.

x: `k7iscool
^x
0

x: `
^x / output of 1 indicates that x is now null
1



15) # take|shape count                        

x: 10 20 30 40 50 60
3 # x
10 20 30

10 # x / Notice x is of length 6; result wraps
10 20 30 40 50 60 10 20 30 40


(3;2) # x / creates a three row, two column matrix
(10 20;30 40;50 60)


(3;10) # x / creates a three row, 10 column matrix (with wrapping)
(10 20 30 40 50 60 10 20 30 40;50 60 10 20 30 40 50 60 10 20;30 40 50 60 10 20 30 40 50 60)

/ Unary # counts the lengths of lists

 x
10 20 30 40 50 60
 
 # x / number of elements in x
6
 
 y: 9 8 5
y 
9 8 5
 z: (x;y)
z 
(10 20 30 40 50 60;9 8 5)
 #:'z / counts each list
6 3



16) _ drop|cut   floor                       

 x: 10 20 30 40 50 60
 3 _ x / cut away 3 elements from the beginning
40 50 60
 
 10 _ x / Notice x is of length 6; so this eliminates more than necessary
!0
/ !0 means an empty list



/ Now unary _ is the floor operator

 15 % 4
3.75
 _ 15 % 4
3


17) $ cast|+/*   string   



 ` $ "abc" / cast string to symbol (name) 
`abc

 . "18" / cast string to int
18
  . "18.2" / cast string to float
18.2

/ Unary form

$ `abc / cast symbol to string
"abc"


18) ? rand|find  unique  

/ Random as discussed in section 1

10 ? 12 / with replacement (can be duplicates) from 0 to 11
5 10 9 11 7 4 4 0 10 8


15 ? 12 / there can be more elements (15) than the domain (0 to 11)
1 9 6 4 10 8 3 1 7 4 1 10 8 1 9

-10 ? 12 / random and uniform without replacemnt (no duplicsates)
3 4 8 1 10 5 0 6 2 11

/ Unary ?
-15 ? 12 / get an error
    ^
length error

? 7 / random between 0 and 1 (uniform)
0.9273194 0.6828101 0.03424805 0.8313162 0.9028654 0.6049852 0.6176891

/ With list as left argument we can find the index of the first match

 40 20 30 10 20 30 ? 30
2

/ Unary ? removes duplicates but preserves order

 ? 40 20 30 10 20 30
40 20 30 10


19) @ at         type   

 x: 40 20 30 10 20 30
@[x;2 4 5] 
30 20 30

 x / unchanged
40 20 30 10 20 30


 @[x; 2 4 5;: ;  -17 -12 -8]
40 20 -17 10 -12 -8

 x / still unchanged
40 20 30 10 20 30


 f: {[x] x * x}
 @[x; 2 4 5; f] / squares locations 2 4 and 5
40 20 900 10 400 900

 x / still unmodified
40 20 30 10 20 30

 @[x; 2 4 5; f] / squares locations 2 4 and 5
40 20 900 10 400 900


/ Are there ways to modify x with this???
/ Others still to come ???

/ Unary @ finds the type of an object

@ 18
`i

@ "18"
`C

@ `abc
`n

20) . dot        value 

/ Ammend  still to come ???

/ Unary . Can evaluate a string

. "18 + 5"

. "f: {[x] x * x * x}"
f

 . "f[5]"
125

21) abs  (absolute value)

 abs -3.2
3.2
 abs -3.2 4 5.3
3.2 4 5.3

22) log  (natural log, also known as ln or log base e)

log 8

23 exp (exponential on e)

 exp 1
2.718282

 exp 3
20.08554

 log 20.08554
3.0

23) sin (takes its argument in radians)

mypi: 3.14 / a crude approximation of pi

sin[mypi] / should be approximately 0
0.001592653

 sin[mypi % 2] / sin pi/2 is 1, so this is close
0.9999997

24) cos

cos[mypi] / close to -1
-0.9999987


 cos[mypi %2] 
0.0007963267

25) in (membership test)

 5 in 10 20 30 5 6 9 10
1

 5 in 10 20 30 5 6 5 10 / even if there are two instances, still return 1
1

 5 in 10 20 30 50 6 15 10
0


26) bin (binary search assumes ascending sorted order))

 x: 5 * (3 + !10)
 x
15 20 25 30 35 40 45 50 55 60

 x bin 33 / index location that is less than or equal to 33
3

 x bin 35 / index location that is less than or equal to 35 (here, equal)
4

4

27) within  (upper  bound for singleton right hand side lists 
and closed lower and open upper bound for binary right hand side lists)

x: 40 10 20 23 15 16 18

 x within ,20 / less than 20
0 1 0 0 1 1 1




 x
40 10 20 23 15 16 18
 x within 16 23 / between 16 (inclusive) and 23 (exclusive) aka [16..23)
0 0 1 0 0 1 1



/ No unary version


28) ss / substring looking for an exact match

 x: "abcdef"
 x ss "cde" / look for beginning and length of match
,2 3

 x ss "bd" / If there is no match, then is this the return value I want???
0#,0N 0N

y: x, x
 y
"abcdefabcdef"

 y ss "cde" / get all matches as a list
(2 3;8 3)



29) like  (string match with wildcards)

  x: "abcdef"

 x like "ab"
0

 x like "ab*" / allows wildcards
1

 x like "*def" 
1

 x like "*bcd*" / arbitrary length wildcards with *
1

 x like "?bcd*" / ? is a single character substitution

Section 4: Data Types

1) Character strings are simply an array of characters

x: "fast, cool, and really concise"
 #x
30
 x[2 4]
"s,"
 x[<x]
"    ,,aaacccdeefilllnnooorssty"

2) Whereas character stringsh occupy one byte per character, symbols
are hashed and therefore take less space, a useful feature in a large data
application in which a symbol is repeated many times.

 x: (`abc; `defg)
 x
`abc`defg
 #x
2

Here is some guidance in choosing between symbols and characters.
If there are a few distinct character sequences and they are repeated many times
(e.g. a history of all trades where there are only a few thousand
stock symbols but millions of trades),
then symbols are best for operations like sorting and matching.
Otherwise char vectors are probably better especially if you need to look inside.

3) Integers are whole numbers or the null integer 0N

 @ 2 / type of 2 is `i
`i

 @ 34
`i

 @ 0N
`i

 ^ 0N / 0N is null
1

 ^ 18 / any other integer is not
0

4) float as in any other programming language; 0n is the null

 @ 2.3 / type of 2.3 is `f
`f
 
 @ 0n / type of 0n is also `f
`f
 
 ^ 0n / 0n is null
1
 
 ^ 2.3 / anything else is not
0

5) Date format is year.month.day and you can get the day by .z.d

 x: .z.d
x 
2018.08.05

 x + 44
2018.09.18

 .z.d+10?24:00:00 / generate random datetimes
2018.08.06T12:09:21 2018.08.06T07:55:41 2018.08.06T19:35:53 2018.08.06T04:00:35 2018.08.06T15:27:18 2018.08.06T16:45:37 2018.08.06T13:26:16 2018.08.06T15:18:01 2018.08.06T17:43:36 2018.08.06T15:49:24


6) Time format is hour:minutes:minutes.milliseconds

x: .z.t / greenwich mean time
x 
23:19:55.658

 x+ 609 / add to milliseconds
23:19:56.267

  09:30+10?06:30 / generate random times
11:28 11:24 13:56 10:21 14:27 09:34 14:49 13:59 11:05 15:02

7) Dictionaries

/ There are many ways to create a dictionary.

/ From partitions
 mypart: ="many sentences have the letter e very often"
 mypart
" acefhlmnorstvy"!(4 14 19 23 30 32 37;1 16;,11;6 9 12 18 22 25 28 31 34 41;,39;15 21;,24;,0;2 7 10 42;,38;29 35;5 13;8 20 26 27 40;17 33;3 36)

 mypart["e"]
6 9 12 18 22 25 28 31 34 41


/ Creating them directly

 mydict: `bob`carol!(2;3)
 mydict
[bob:2;carol:3]

  mydict[`bob]
2

/ dictionaries can be heteogeneous in their values
 mydict2: `alice`bill`tom`judy`carol!(1 2 3 4; 8 7; 5; "we the people"; `abc)

 mydict2[`carol]
`abc
 mydict2[`judy]
"we the people"

/ dictionaries can be heterogeneous in their keys too

mydict3: (`marie;`jeremie;2)!(34; "hello, world"; 7)
 mydict3
(`marie;`jeremie;2)!(34;"hello, world";7)

/ find the keys of dictionaries is easy:

 ! mydict3
(`marie;`jeremie;2)

/ and the values

 . mydict3
(34;"hello, world";7)

Section 5: Control Flow

Before we get to control flow in the classical
sense, it's important to understand
how  to read a k7 expression. There is no 
precedence as there is in some languages where for example
* binds more than + or -.
Instead the precedence is right to left which in fact
conforms with mathematical usage (e.g., for sum of x * y we first
multiply x and y and then take the sum)

Example:

 20*4-3
20

 (20*4) - 3 / to make * bind closer than -, you need parentheses
77

 20*(4-3) / otherwise, precedence is right to left.
20

x: 90 30 60 40 20 19 / let's say we want the sum of the elements having
 / values greater than 35

x > 35 / put a 1 where values are greater than 35
1 0 1 1 0 0


& x > 35 / indexes that are greater than 35
0 2 3

 x[&x > 35] / elements in x that are greater than 35
90 60 40


 +/ x[&x > 35]  / sum of elements of x whose values are greater than 35
190

2) $[c;t;f]    (Conditional:
if c is true then execute the t branch else the f branch)

x: 3 4 5
y: 10 20 30

 $[5 > 3; +/x; +/y]
12
 $[5 < 3; +/x; +/y]
60


3) ?[x;I;[f;]y] (replace the index positions by what comes afterwards

x: 3 4 5 6 7 8 9 10

y: 100 200 300 400

 ?[x;3;y] / replace what's in position 3 by y
3 4 5 100 200 300 400 6 7 8 9 10

 ?[x;3 4; y] / starting in position 3 and counting 4, replace by y
3 4 5 100 200 300 400 10



Section 6: Input/Output and Interprocess Communication

0) Create a file having these three lines and call it tmp:

We the people
of the
United States

1) Read in the file
 x: 0: "tmp"
 x
("We the people";"of the";"United States")

 x[1] / x is just an array so x[1] is the second element
"of the"

 y: (x[0]; x[1]; x[2]; x[1])
 y
("We the people";"of the";"United States";"of the")


 "tmp2" 0: y
"tmp2"

Now look at tmp2 and see that you have:

We the people
of the
United States
of the

2) 1: (write binary image)

x: 1 2 3 4
"tmp3" 1: x

y: 1: "tmp3"

y

3) Text input/output is 2: 

 "foo"2:("This is line 1\n This is line 2")
"foo"

 2:"foo"
"This is line 1\n This is line 2"


4) 1:""1:"prompt" ??? I don't know how this works

Section 7: Data Structures

k has atom, list (2;`c), dict [a:2;b:`c] and func {[x;y]x+y}
dict [a:2;b:`c]
view f::32+1.8*c TODO

Section 8: Debugging

on error(inspect locals etc.)
' up
\ out
2+ \3  trace

Section 9: Meta-functions
 

1) \l a.k  load   

create a file foo.k with the two lines
x: 1 2 3 4
f: {[x] x*x}

Then start a k7 session and then in that session:
 \l foo.k
 x
1 2 3 4
 f
{[x] x*x}

2) \v variables  \f functions 

 \l foo.k

 \v
,`x

 \f
``f

3) \w workspace / how much memory are you using

 \w
704

4) \d directory (go into subdirectory). What's defined in directory is not
defined in the subdirectory.

\l foo.k

\v 
,`x



\d mysub 

\v 
0#,`

5) \a doesn't work


Section 10: Tables

In the row-wise vs. column-wise table debate, k7 comes out as columnwise.
We'll work up to this slowly.

Consider a list:
 x: 1 2 3 4 5 10 15
 x
1 2 3 4 5 10 15

Create a one column table from this:

 xtab: +`numcol!x
 xtab

 xtab
 ol
 --
  1
  2
  3
  4
  5
 10
 15

Here the table has one column and its header is numcol.

  select numcol from xtab
 ol
 --
  1
  2
  3
  4
  5
 10
 15

  select sum numcol from xtab
 ol
 --
 40

   select sum numcol from xtab where numcol > 4
 ol
 --
 30

Ok, now let's create a multiple column table.

n: 7
newtab: +(`stock`date`price`vol)!(n ? `ibm`goog`hp;.z.d+n?16:00:00;100 + n?200; n?5000)
 newtab
 stoc                date ice  vol
 ---- ------------------- --- ----
 ibm  2018.08.25T11:28:14 285 3016
 hp   2018.08.25T14:59:27 236 1988
 ibm  2018.08.25T07:49:46 106  820
 ibm  2018.08.25T05:31:15 266 4316
 ibm  2018.08.25T00:55:02 280 3596
 goog 2018.08.25T00:42:11 220  650
 goog 2018.08.25T06:59:28 223 4136

 select sum price*vol by stock from newtab
 stoc|     vol
 ----| -------
 goog| 1065328
 hp  |  469168
 ibm | 3101416

  select sum price*vol by stock from newtab where date > 2018.08.25T10:00:00
 sto|    vol
 ---| ------
 hp | 469168
 ibm| 859560

User-defined functions:

f:{[x] 1.5*x}
 select sum f[price*vol] by stock from newtab where date > 2018.08.25T10:00:00
 sto|     vol
 ---| -------
 hp |  703752
 ibm| 1289340


Extracting Data from Tables into Other Structures


/ select always gives a table
     select date from newtab
                date
 -------------------
 2018.08.25T11:28:14
 2018.08.25T14:59:27
 2018.08.25T07:49:46
 2018.08.25T05:31:15
 2018.08.25T00:55:02
 2018.08.25T00:42:11
 2018.08.25T06:59:28

 
/ exec on a single column gives a list
     exec date from newtab
2018.08.12T02:46:46 2018.08.12T01:29:13 2018.08.12T02:47:22 2018.08.12T05:56:38 2018.08.12T06:38:54 2018.08.12T00:15:57 2018.08.12T00:44:10 2018.08.12T15:16:50 2018.08.12T07:37:14 2018.08.12T03:17:45

      exec date from newtab where stock=`ibm
2018.08.12T01:29:13 2018.08.12T02:47:22 2018.08.12T06:38:54 2018.08.12T00:15:57 2018.08.12T15:16:50 2018.08.12T07:37:14

  mydict: exec sum price*vol by stock from newtab where vol > 60
 mydict
[goog:408552f;hp:1249725f;ibm:2353486f]

 mydict[`goog]
408552f

Importing from a csv file

Create a small csv file mytrade.csv whose schema is:
tradeid,stock,timeindicator,price,vol


mytrade.csv:
1,goog,50,1237,100
2,msft,51,109,100
3,goog,52,1240,200
4,msft,53,112,200


  ("iciii";",")0:"mytrade.csv"
(1 2 3 4;"gmgm";50 51 52 53;1237 109 1240 112;100 100 200 200)

mytrade1: +(`tradeid`stock`timeindicator`price`vol)!("iciii";",")0:"mytrade.csv"

 select tradeid, price, vol from mytrade1 
+`tradeid`price`vol!(1 2 3 4;1237 109 1240 112;100 100 200 200)

  select tradeid, price, vol from mytrade1  where price > 500
+`tradeid`price`vol!(1 3;1237 1240;100 200)


Then one with proper datetimestamps:

1,goog,15:16:50,1237,100
2,msft,15:16:51,109,100
3,goog,15:18:50,1240,200
4,msft,15:18:52,112,200

mytrade2: +(`tradeid`stock`time`price`vol)!("ictfi";",")0:"mytradebac2.csv"

   select tradeid, time, price, vol from mytrade2  where price > 500
+`tradeid`time`price`vol!(1 3;15:16:50.123 15:18:50.124;1237 1240f;100 200)

   select sum price * vol by time.minute from mytrade2  



Group by on times (doesn't work yet) ???

 select time from mytrade2
+(,`time)!,15:16:50.123 15:16:51.109 15:18:50.124 15:18:52.112

 select time.minute from mytrade2
select time.minute from mytrade2
^

Asof (need help on this)???


Keyed Tables

  newtabkeyed: `tradeid key newtab
 
 newtabkeyed
(+(,`tradeid)!,!10)!+`stock`date`price`vol!(`goog`ibm`ibm`hp`ibm`ibm`hp`ibm`ibm`hp;2018.08.12T02:46:46 2018.08.12T01:29:13 2018.08.12T02:47:22 2018.08.12T05:56:38 2018.08.12T06:38:54 2018.08.12T00:15:57 2018.08.12T00:44:10 2018.08.12T15:16:50 2018.08.12T07:37:14 2018.08.12T03:17:45;174 127 167 112 219 225 150 202 257 239;2348 3925 2790 4807 560 3233 1127 704 1544 2269)

 select tradeid,stock,date,price from newtabkeyed where tradeid=3
select tradeid,stock,date,price from newtabkeyed where tradeid=3
^
tradeid error




Section 11: Shortcuts

1) We would be remiss to fail to mention some shortcuts that k7 afficionados
love to use, even though some of us feel that they reduce clarity.
For example, unary functions implicitly perform "each" when applied
to arrays. For example,

f:{[a] (a*a)+3 }

 f'1 2 3 4
4 7 12 19

 f 1 2 3 4
4 7 12 19

 x
(1 2 3 4;5 6 7 8)
 f'x
(4 7 12 19;28 39 52 67)
 f x
(4 7 12 19;28 39 52 67)

2) default function parameters are x y z, e.g. {z+x*y}[3;2;1] is 7

 f:{z + x*y}
 f[10; 20; 30]
230

3) Eval

It is possible to evaluate strings as we have seen

. "2+3"

but also to evaluate parse trees


 !(::;`x;7 8)  / x:7 8
 x
7 8

 !(+:;`x;20 30) / x: 27 28
 x
27 38

Section 12: System Calls (in progress)

e.g. instead of \ls \du \wc -l try

Unix ls is just \ff ?.c

Unix du is \fk ?.c

Unix wc -l is \fl ?.c

Section 13: A gallery of exercises/examples.

These examples are going to start from a database of trades.

n: 100

secid: n ? (`goog;`facebook;`ibm;`msft)
price: 100 + n ? 200
vol: 10 + n ? 1000
time: !n



1) Find all trades such that the price is over 175.

ii: & price > 175

z: secid[ii] ,' price[ii] ,' vol[ii] ,' time[ii]

z[5]

2) Find the high and low of each security.

mydict: = secid
names: ? secid

maxmin:{[name] name , (|/price[mydict[name]]), (&/price[mydict[name]])}

maxmin'names

/ or to be able to take an arbitrary dictionary
maxmin2:{[name;somedict] name , (|/price[somedict[name]]), (&/price[somedict[name]])}

 maxmin2[;mydict]'names
((`facebook;296;100);(`goog;290;102);(`msft;289;128);(`ibm;294;117))

3) Get the moving average of each security

mavg:{[name] name, (+\price[mydict[name]])%'(1+!#mydict[name])} 
mavg'names

4) Determining the finishing time of each task if you do them
in earliest deadline first order.

n: 10
taskid: !n
tasktime: 2 + n ? 20
deadlines: 40 + n ? 50

 tasktime
11 20 17 21 14 9 9 2 19 16

 deadlines
65 56 80 48 72 74 67 71 76 72

/ Put them all together

 taskid,'tasktime,'deadlines
(0 11 65;1 20 56;2 17 80;3 21 48;4 14 72;5 9 74;6 9 67;7 2 71;8 19 76;9 16 72)


/ Now determine the order of deadline indexes
/ for the deadlines to be in order.  
 inddead: < deadlines    
 deadlines[inddead]
48 56 65 67 71 72 72 74 76 80

/ Put the tasks in the same order
 taskid[inddead]
3 1 0 6 7 4 9 5 8 2

/ Put the task times  in the same order

 tasktime[inddead]
21 20 11 9 2 14 16 9 19 17

/ Put all of them in the same order
 taskid[inddead],'tasktime[inddead],'deadlines[inddead]
(3 21 48;1 20 56;0 11 65;6 9 67;7 2 71;4 14 72;9 16 72;5 9 74;8 19 76;2 17 80)

/ Find end point if tasks are executed in this order

 +\tasktime[inddead]
21 41 52 61 63 77 93 102 121 138

/ Determine which deadlines are met (1) and which aren't (0)
 deadlines[inddead] > +\tasktime[inddead]
1 1 1 1 1 0 0 0 0 0

/ Determine which taskids have their deadlines met
 taskid[inddead][& deadlines[inddead] > +\tasktime[inddead]]
3 1 0 6 7

5) Debugging


 fib:{[n] fib[n-1] + fib[n-2]}

 fib[5]
{[n] fib[n-1] + fib[n-2]}
                ^
stack error

To debug this, we can do several thing.
First, just query the variables, e.g. 

> n
-189

We might realize that n should never be negative.
Another thing we can do is store all the values of n in this recursive
function.


 out: ()
fib:{[n] out,: n; fib[n-1] + fib[n-2]}
fib[5]  
{[n] out,: n; fib[n-1] + fib[n-2]}
                         ^
stack error

But now we can query out:

> out
5 3 1 -1 -3 -5 -7 -9 -11 -13 -15 -17 -19 -21 -23 -25 -27 -29 -31 -33 -35 -37 -39 -41 -43 -45 -47 -49 -51 -53 -55 -57 -59 -61 -63 -65 -67 -69 -71 -73 -75 -77 -79 -81 -83 -85 -87 -89 -91 -93 -95 -97 -99 -101 -103 -105 -107 -109 -111 -113 -115 -117 -119 -121 -123 -125 -127 -129 -131 -133 -135 -137 -139 -141 -143 -145 -147 -149 -151 -153 -155 -157 -159 -161 -163 -165 -167 -169 -171 -173 -175 -177 -179 -181 -183 -185



6) Order-based Relational Algebra
This version is build just on arrables (tables consisting of lists of
ordered lists (arrays)).
First we review selects, projects, and moving aggregates.
Then we show equi-joins then general joins.
file: arrable.k

/ FUNCTIONS


/ given a set of indexes give me those values of a vector x
indtoval:{[x;i] @[x;i]}

/ given a bunch of lists alllist
/ a selection string on alllist selstr
/ (a typical selstr might be "(alllist[1] > 3 ) & (alllist[0] < 40)" )
/ and a set of output columns outlist
/ Output: after selecting based  on selstr, output columns cols of alllist
mysel:{[alllist; selstr; outlist] ii: & . selstr;indtoval[;ii]'alllist[outlist]}



/ given a bunch of lists alllist
/ a subset to sort by sortby
/ other lists to follow that sort outlist
/ Output: based on the sort order of alllist[sortby] 
/ create rows of outlist in order
myasc:{[alllist; sortby; outlist] myind: $[1 < #sortby; < +alllist[sortby]; < alllist[*sortby]]; indtoval[;myind]'alllist[outlist])}



/ This does moving sum on numpoints (e.g. three point moving sum)
/ of the array myarray
/ If there are fewer than numpoint in myarray, it does the moving sum up
/ to the number of points in myarray.
movsum:{[numpoints;myarray] x: +\myarray; xsub: $[numpoints < #myarray;(numpoints # 0),x[!(#x)-numpoints];0]; x - xsub}

/ This does moving average on numpoints (e.g. three point moving average)
/ of the array myarray
/ If there are fewer than numpoint in myarray, it does the moving average up
/ to the number of points in myarray.
movavg:{[numpoints;myarray] x: movsum[numpoints; myarray]; mydivs: $[numpoints < #myarray; (1+!numpoints), numpoints _ (#myarray) # numpoints;(1+!#myarray)]; x%mydivs}

/ relational equijoin on one attribute
/ given two lists of lists LL1 and LL2
/ index from LL1 indLL1
/ index from LL2 indLL2
/ indexes from LL1 outLL1 
/ indexes from LL2 outLL2 
/ Find all indexes of LL1 and indexes of LL2 that match
/ based on the values in indLL1 and indLL2 and then take the cross product
/ for the columns outLL1 of LL1 and outLL2 of LL2
eqjoin:{[LL1; LL2; indLL1; indLL2; outLL1; outLL2] mymatch: &:' LL1[indLL1] =\: LL2[indLL2]; outindLL1: ,/ ((#:')mymatch) #' !#LL1[indLL1]; outindLL2: ,/ mymatch; (indtoval[;outindLL1]'LL1[outLL1]) , (indtoval[;outindLL2]'LL2[outLL2])}

/ Below is unused (and needs to be debugged) until we can get longer functions

/  mycross:{[pair; mydict1; mydict2] x: pair[0]; y: pair[1]; ,/mydict1[x] ,/:\: mydict2[y]}

/  fin:{[allmatches; Ll1; LL2; outLL1; outLL2] (indtoval[;allmatches[;0]]'LL1[outLL1]), (indtoval[;allmatches[;1]]'LL2[outLL2])}

/  eqjoindict:{[LL1;LL2;indLL1;indLL2;outLL1;outLL2] d1: = LL1[indLL1]; keys1: ! d1; d2: = LL2[indLL2]; keys2: ! d2; mym: keys1 ? keys2; pairs: (mym,'keys2); pairs@: & pairs[;0] < #keys1; mm: ,/mycross[;d1;d2]'(keys1[pairs[;0]],' pairs[;1]); fin[mm; LL1; LL2; outLL1; outLL2]}



/ DATA AND EXECUTION

indata: (3 4 3 4 3 9 9 9 9 9 9;30 40 30 40 30 90 90 90 90 90 90;7 9 1 2 1 2 3 4 8 7 3)

mysel[indata; "indata[1] > 60 "; 0 1 2]


x: myasc[indata; 2 1; 0]
x

movavg[3;x]

/ can combine these

x1: mysel[indata; "indata[1] > 35 "; 0 1 2]

x2: myasc[x1; 2 1; 0]

movavg[3;x2]

/ Now look at the equijoin

LL1: indata

LL2: (300 400 300 400 300 800 800 800 301 401 402;30 40 30 40 30 80 80 80 30 40 40;7 9 1 2 1 2 3 4 8 7 3)

eqjoin[LL1; LL2; 1; 1; 0 1; 0 1]

/ Sometimes we want to perform a join, but get results only for one argument
/ e.g. LL1 in this case:


y1: eqjoin[LL1; LL2; 1; 1; 0 1 2; ()]

y2: mysel[y1; "y1[1] > 35 "; 0 1 2]

y3: myasc[y2; 1; 2]

movavg[3;y3]
