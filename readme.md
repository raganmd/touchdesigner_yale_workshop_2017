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
12:30 - 1:30 | SOPs, and Real Time Rendering |
1:30 - 2:00| Intro to Python in Touch |
2:00 | **Offical End of Day**
2:00 - 4:00 | Open ended work / consultation time

### Overview of the Day ###

#### Introductions


#### Navigating the Network


#### TOPS

#### Sweet 16

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

#### Sweet 16

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


#### Introduction to Python in TouchDesigner


---

## Day 2  
_1.6.17_

Time | Topic
---|---|
9:00 - 10:00 | Building your First Playback System |
10:00 - 11:00 | Building a VJ System |
11:00 - 12:00 | Tracking Performers with a Kinect |
12:00 - 12:30 | **LUNCH** |
12:30 - 1:00 | Advanced Rendering Techniques - Instancing |
1:00 - 2:00| Best Practices and Optimization |
2:00 | **Offical End of Day**
2:00 - 4:00 | Open ended work / consultation time

### Overview of the Day ###

#### Building your First Playback System


#### Building a VJ System


#### Tracking Performers with a Kinect


#### Advanced Rendering


#### Best Practices and Optimization


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
