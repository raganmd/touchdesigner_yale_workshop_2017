# Yale Workshop 2017 #
---

### Matthew Ragan ###
_[matthewragan.com](http://matthewragan.com)_  
_1.5.17_

---
## Day 1  
_1.5.17_

Time | Topic
---|---|
9:00 - 9:30 | Introductions |
9:30 - 10:30 | Navigating the Network |
10:30 - 12:00 | TOPs and CHOPs |
12:00 - 12:30 | **LUNCH** |
12:30 - 1:00 | Intro to Python in Touch |
1:00 - 2:00 | Building your First Playback System |
2:00 | **Offical End of Day**
2:00 - 4:00 | Open ended work / consultation time


### Overview of the Day ###

#### Introductions
I have a plan for how we're going to use our time over the next two days, but sometimes plans need to change. We're going to start by taking a few minutes to get to know who is in the room - this way I can get a sense of if we're on the right track for the next two days or if I need to help us shift course.

#### Navigating the Network
Welcome to the TouchDesigner network. The Network is the name for the open space where we layout our nodes, and create chains of operators. We can zoom, pan, and navigate the network like a hierarchy. We can also expose lots of different viewports from here. We aren't going to spend too much time talking about how to navigate the network abstractly - since it's easiest to learn by actually working on a project - but it is handy to know a few things to help us get started.

What is an operator?! If you're familiar with Object Oriented Programming, we can almost think of our operators as an instance of an object. If you're not familiar with OOP (I wasn't when I started) that's okay. We can think of an operator as a building block for our networks. How we arrange our building blocks changes what our final results are, and how we structure our projects can make it harder or easier at the end of the day to know what's going on. In general, we are going to focus on building clean, modular, and reusable networks. It's often tempting to feel like you need to make something unique for every show or installation, but in fact we end up being much happier programmers if we're able to re-use pieces of our code. Over the next two day we're going to step into a strange head space. We're no longer just designers, we now have to think of ourselves as programmers and engineers. It's not enough to have a creative vision, we know have to consider what implementation means in our design. 

"But Matt, forcing me to think about the engineering is going to hamper my creative process! I just want to create without boundaries." Good for you. These days I don't usually let myself be limited by what's possible technically; however, when we're starting to think about interactivity and developing new tools we need to start from somewhere - and our somewhere relies on making sure we have a common understanding of the computational processes and principles that will define what we can ask a computer to do. In designing a production we often wrestle with various constraints - the play is a constraint, the space is a constraint, the time, the set, and and and. Design is inherently a process of wrestling with constraint, so let's think of our knowledge of this field as just another constraint for the time being. Rather than thinking of how we're limited by the realities of current technology, we might instead think about how knowing the rules of a given system allow us to find ways of working around them or flat out exploiting them. 

#### TOPS

TOPs - short for Texture Operators - are the pixel engine of our environment. What does that mean, "Texture?" Texture operators owe their namespace to the fact that to your computer a set of pixels, especially in conjunction with a graphics card, is called a texture. Texture operations are how we manipulate pixels, and especially how we think about manipulating pixels with GLSL. Nearly all of our TOPs are, under the hood, GLSL wrapped up to look like an operator. GL is especially fast as it's usually run on your graphics card. These operations happen in parallel and are therefore fast. So fast, in fact, that we usually don't have to think about the computational cost of TOPs. There are many exceptions to this rule, but as we get started these operators are the ones that need the least attention from us when it comes to thinking of optimization.

We're going to take some time to talk about TOPs and play with creating networks of them. Derivative usually encourages new programmers to look over the top 16 ops that are essential ingredients to working with these operators. We won't cover all of them, but they're worth looking over when you have time.

**Sweet 16**

TOP | Purpose
---|---|
Movie File In | Read movies, still images, or a sequence of still images.
Ramp | Create vertical, horizontal, radial, and circular ramps.
Level | Adjust contrast, brightness, gamma, black level, color range, opacity.
Transform| Translate, scale, rotate, multi-repeat tile, background fill.
Over | Place and shift one image over another based on the alpha of one image.
Text | Text generation with variety of fonts.   
Blur | Blur.
Composite | Combine multiple images with variety of operations like under, difference.  
Render | Render 3D objects, lights and camera into an image.
CHOP to | Convert CHOP channels into scanlines of an image. 
Resolution | Change the resolution of an image and smooth-filter down.  all TOPs alter resolution
Crop | Crop image to smaller resolution.
Select | Selects an image from the same network or a different network.
Reorder | Re-order the channels of an image.
Cache | Hold a static or dynamic sequence of images and output one of them.
Displace | Use red-blue of one image to warp another image.

#### CHOPS

CHOPs - short for Channel Operators - are the control engine of this environment. There's lots to cover here, but to help us get started it's important to think about channels and samples as being distinct from one another. This can be a bit of a tricky concept, but it's well worth taking some time to think through how these differ. Let's, for a moment, think about channels and samples as though they were beads on a string. Each string is a different channel. A string can hold lots of beads. All of the beads on the same string are connected to one another positionally. That is to say that on a single string we can differentiate the third bead from the fourth. Using this metaphor we can think of channels as being the string, and beads as being samples. Try on that idea for a little bit, and remember to come back to it as we talk more and more about channels and samples. 

For now we'll start by looking at how we can connect CHOPs in series to build control and animation systems. Derivative usually encourages new programmers to look over the top 16 ops that are essential ingredients to working with these operators in general. We won't cover all of them, but they're worth looking over when you have time.

**Sweet 16**

CHOP | Purpose |
---|---|
Constant | Create new channels.
LFO | Low Frequency Oscillator.
Noise | Create semi-random patterns.    
Select | Grab a channel from any other CHOP.
Merge | Merge channels from two or more CHOPs.
Math | Add, multiply or scale channels.
Lag | Smooth and delay a channel.
Speed | Use speed to calculate distance.
Lookup | Use one channel to get values from another CHOP.
Trail | Watch a time-history of CHOP channels.
SOP to | Record a time-history of channels.  DAT to, TOP to
Limit | Restrict channels to a range or certain step values.
Audio Device In | Get audio from input device.
OSC In | Open Sound Control, MIDI.
Panel | Get state, u, v etc values from any panel gadget. 
Timer | Run timers, loops, delays and trigger events.

##### References and Exports

There are two major ways to connect operators of dissimilar families together in TouchDesigner. We can use both references (written in as Python expressions) or exports from tables or CHOPs. If you're scratching your head that's okay. We've already seen that operators of similar families can be connected with wires, but operators of dissimilar families need to be connected with exports or references. This means we can drive attributes of a given object with another object. 

That's all well and good Matt, but why are there two different ways? Well, that's a good question. I wish there was a simple straightforward answer, but like many things in the world, it's a little murky. Python is excellent for huge number of tasks. It's also far more flexible (in my opinion at least), and generally simpler to set up. While that may be true, it's also less efficient than exports. So... what is a person to do?! The honest answer is learn both. I often start with Python references and then move to exports during my final optimization steps on a project. Though much of this often depends on the project, the installation, and the complexity of the job. We're going to learn a bit of both.

[Understanding references part 1](https://matthewragan.com/2014/06/01/understanding-referencing-touchdesigner/)  
[Understanding references part 2](https://matthewragan.com/2014/06/27/understanding-referencing-part-ii-touchdesigner/)  
[Writing references with Python](https://matthewragan.com/2015/10/19/python-in-touchdesigner-writing-python-references-touchdesigner/)  

#### Introduction to Python in TouchDesigner

We're not going to do a full Python course - we just don't have the time - but we are going to cover some essential principles that we often need when doing any Python scripting in touch. Before we get there, it's worth thinking about why we need to learn a scripting language. 

**Why Python Anyways?!**

Scripting lets us extend what we can do in Touch beyond using just the operators in our networks. Why? Well, that's a reasonable question to ask, and when the rubber meets the road we often need do a few things in a script based approach to make sure everything goes the way we want. Using Python we have access to a whole different set of tools to determine when operations occur, change parameters on operators, and any number of actions. A little bit of Python can go a long way, and while I often need to write out more complex classes for large scale projects, we can start by getting our feet wet with a few essential ingredients.

**Printing**

Printing is our way to see what's happening in our code. Printing is the best way we have to debug what's happening in our Python, and it's part of the reason we start here. In TouchDesigner when we print out something it shows up in the text port. We're going to take a hot second to locate the text port, and then see how our messages end up there when we print them.

**Variables and Logic**

Take a moment and remember back to your Algebra 1 class. Let's take a look at an equation:
```
f(x) = 2 * x
```
In algebra x is our variable. It stands in for any possible number, right? So if x = 10, then the result of our function is 20. We can use this same idea as the starting point for understanding variable in a programming language. Variables allow us to write abstract code, but unlike Algebra, our variables are far more flexible (more on that later). For now we can use this idea to help us do some logic. 

Let's write a simple logical test to see how this might work. We want to know which of two numbers is larger - number 1 or number 2. We're going to practice this with variables, so let's start by writing out our two variables:

```python
var1 = 3
var2 = 10
```

Next we'll use a simple logical test to print out which number is larger:

```python

if var1 > var2:
    print( 'var1 wins' )

else:
    print( 'var2 wins' )
```

This is pretty good, but it leaves out an essential possibility... what if both numbers are the same?! Let's add one more logical test to account for that possibility:

```python
var1 = 3
var2 = 3

if var1 > var2:
    print( 'var1 wins' )

elif var1 == var2:
    print( 'We got a tie kids!' )

else:
    print( 'var2 wins' )
```

**Loops**

Loops let us simplify code that might otherwise be tedious to write. Okay, using what we've learned so far, let's print out all the numbers between 0 and 10 - but not including 10. Better yet, let's include something like "this is number " before the number. If we do that the long hand way it might look like;

```python
print( "This is number 0" )
print( "This is number 1" )
print( "This is number 2" )
print( "This is number 3" )
print( "This is number 4" )
print( "This is number 5" )
print( "This is number 6" )
print( "This is number 7" )
print( "This is number 8" )
print( "This is number 9" )
```

Okay, that's not so bad, but what if we wanted to do that up to 100, or 1000, or 10,000. You get the idea, doing this the long way doesn't scale well. So, what's the better way? The better way is to write a loop that will execute the same code for all of the values in a given set. Let's look at what that might be in Python:

```python
for item in range( 0,10 ):
    print( item )
```

The code above just prints the item, but we can modify it to be just like our first example:

```python
for item in range( 0,10 ):
    print( "This is number ", item )
```

So what's happening here? Our simple for loop uses the word "item" to stand in for a variable that increments every-time we go through the loop. Our range determines our starting and ending points. We can write this in a way that's a little cleaner by using a variable instead of those bounding values:

```python
num_loops = 10

for item in range( num_loops ):
    print( item )
```

**Methods/Functions**

Nice work! Now lets' look a little at functions. Functions let us write a little piece of reusable code that we can come back to. These can be very handy in TouchDesigner, especially if there's something that we know we'll need to do from time to time. Just like earlier when we were talking about functions in relationship to algebra to understand variables - now let's go a step farther and see how we can write that same algebraic function in Python.

Algebra
```
f(x) = 2 * x
```

Python
```python
def my_function( value1 ):
    result = 2 * value1
    return result
```

That's a little different from the Algebra, so let's pull apart what's happening. First we specify that we're defining a function called my_function - that's what's happening when we use "def" in front of our function name. Next we can specify that this function takes an argument - this is what's in our parenthesis. A colon specifies what's inside of the function. Here I'm create a new variable, "result", that's our input value * 2. Finally we return our new variable with a return statement. If we didn't use a return statement our value would still be calculated, but it wouldn't be accessible to use outside of the function. Let's use this same idea in conjunction with what we did earlier. 

Let's start by turning our logic test into a function. After we do that, let's run the function as a part of a for loop.

```python

# here we're going to start by writing out our new function
def my_method( my_var1, my_var2 ):
    
    if my_var1 > my_var2:
        print( 'var1 wins' )

    elif my_var1 == my_var2:
        print( 'We got a tie kids!' )

    else:
        print( 'var2 wins' )

# next we define a variable for our loop - how many loops that is
num_loops = 10

# finally we run the loop
for item in range( 10 ):
    my_method( item, 5 )

```

**Targeting Operators**

Nearly every parameter in TouchDesigner can be scripted. That's handy because it means we can use python to make lots of changes based on user inputs or logic tests. This creates a whole new area of possibilities for us, one that honestly took me a little too long to really understand. We're going to start by looking at how we can change the value of a parameter on a constant CHOP.
 
Looking at our constant CHOP, if we look at parameters we can see on the left hand side that it says value0 on the left hand side of the parameter window. This also happens to be parameter name we can use in python to access this parameter.

Let's change this value to a different number to see this in action.

```python
op( 'constant1' ).par.value0 = 10
```

With the script above we're able to change a value in one of our operators. We'll take a closer look at this technique, and how we can better take advantage of it as we build out a simple playback system.

#### Building your First Playback System

While all of the concepts above a great in principle, they're difficult to understand outside of the context of what they do, and they they work together. We'll use the rest of our time today to build out a simple playback system for pre-made video. Playing back files is one of the essential ingredients in working with any programming language in a performance setting, so we'll take the concepts we learned today and apply them in practice. 

#### End of Day 1

I know you're all hungry for more programming, and so am I. I'm available for the next 2 hours to answer questions, look over work, help you do some programming, or talk through how to actualize a concept you've been thinking about. 

_documentation written in markdown_