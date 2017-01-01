# Yale Workshop 2017 #
---

### Matthew Ragan ###
_[matthewragan.com](http://matthewragan.com)_  
_1.5.17_

---

## Summary   

Join Matthew Ragan from [Obscura Digital](http://obscuradigital.com/) for a whirlwind tour of what goes into working as a creative coder. Over the course of two full days students will learn the fundamental principles and organizational flow of working in [Derivative's TouchDesigner](http://derivative.ca/) - for the uninitiated, TouchDesigner is a node based programming environment used in installations, live events, and museums internationally. This workshop will largely be focused on the intersection of art / design and the development of new tools for live performance. While there are a growing number of tools for media playback in live events, there are precious few for creating dynamic and generative artwork. In this workshop we will look at both how to playback traditionally made content, as well as how to build generative real-time rendered environments. More than just a flash and trash demo, this workshop aims to help familiarize students with a development environment as well as examine the challenges and opportunities when designing real-time systems.

Students can expect to walk away from the workshop with:

* an understanding the development environment
* best practices for development and organization
* foundational principles for playing and cueing traditional media
* foundational principles and experience creating generative artwork
* experience tracking performers (both with a kinect and with traditional computer vision techniques)
* an overview of techniques for building user interfaces for interactive systems
* an introduction to Python as a scripting language. 

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

##### References


##### Exports


#### Introduction to Python in TouchDesigner


#### Building your First Playback System

While all of the concepts above a great in principle, they're difficult to understand outside of the context of what they do, and they they work together. We'll use the rest of our time today to build out a simple playback system for pre-made video. Playing back files is one of the essential ingredients in working with any programming language in a performance setting, so we'll take the concepts we learned today and apply them in practice. 

#### End of Day 1

I know you're all hungry for more programming, and so am I. I'm available for the next 2 hours to answer questions, look over work, help you do some programming, or talk through how to actualize a concept you've been thinking about. 


---

## Day 2  
_1.6.17_

Time | Topic
---|---|
9:00 - 10:00 | SOPs, and Real Time Rendering |
10:00 - 11:00 | Advanced Rendering Techniques - Instancing |
11:00 - 12:00 | Building a VJ System |
12:00 - 12:30 | **LUNCH** |
12:30 - 1:30 | Tracking Performers with a Kinect |
1:30 - 2:00| Q&A and Offical Wrap | Other Resources
2:00 | **Offical End of Day**
2:00 - 4:00 | Open ended work / consultation time

### Overview of the Day ###

#### SOPS


#### Sweet 16

SOP | Purpose
---|---
Circle | Circle, sphere, torus primitives.
Grid | Grid, box, rectangle.
Merge | Merge and delete.
Copy | Copy or replicate.
Switch | Switch or blend multi-inputs.
Texture | Apply texture coordinated to points or vertices.
Noise | Apply noise, twist and deform.
Transform | Transform point positions.
DAT to | DAT table to SOP points.
CHOP to | CHOP channel samples to SOP points.
Trace | Trace a TOP image to polygons.
Clip | Clip and carve.
Facet | Facet, subdivide, convert.
Particle | Particles.   
Sweep | Sweep, skin, rails.
Sort | Sort and reorder.

#### Realtime Rendering


#### Building a VJ System


#### Tracking Performers with a Kinect


#### Advanced Rendering


#### Best Practices and Optimization


#### End of Day 2

## Online Materials ##
[GitHub Repository | touchdesigner_yale_workshop_2017](https://github.com/raganmd/touchdesigner_yale_workshop_2017)

## Additional Support Materails ##
[ Matthew Ragan's TouchDesigner Teaching Materials ](https://matthewragan.com/teaching-resources/touchdesigner/)  
[nvoid | Introduction to TouchDesigner ](https://www.gitbook.com/book/nvoid/introduction-to-touchdesigner/details)  
[ Ian Shelanskey's Examples ](https://ianshelanskey.com/)  
[ Dr. Indae Hwang's Examples ](http://www.indaehwang.com/category/touchdesigner/)  
[ Grady Sain's OP Tutorials ](http://www.interestingresults.com/)  
[ Matthew Ragan's Examples based on Forum Questions ](https://github.com/raganmd/td_fb_forum_examples)  
[ Offical TouchDesigner 088 Wiki ](http://www.derivative.ca/wiki088/index.php?title=Main_Page)  
[ Offical Derivative Tutorials Page ](http://www.derivative.ca/wiki088/index.php?title=Category:Tutorials)

_documentation written in markdown_
