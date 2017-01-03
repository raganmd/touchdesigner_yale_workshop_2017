# Yale Workshop 2017 #
---

### Matthew Ragan ###
_[matthewragan.com](http://matthewragan.com)_  
_1.5.17_

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

Surface Operators are the geometry engine of TouchDesigner. SOPs let us create worlds, geometries to manipulate, and on and on. We can both import geometries, and create our own. Today we're gonna start by getting a handle on how SOPs work in TouchDesigner so we can do some real time rendering. 

For now we'll start by looking at how we can connect SOPs in series to build geometry and environments. Derivative usually encourages new programmers to look over the top 16 ops that are essential ingredients to working with these operators in general. We won't cover all of them, but they're worth looking over when you have time.

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

#### Realtime Rendering - Beginning and Intermediate Skills

There's lots to cover in realtime rendering and we're not going to get to all of the things this time - BUT, we can give it a good start. Out the gate we're going to talk about how to set up rendering networks, what our various lighting options include, as well as how our camera works.

Once we have a bit of that under our belt we're going to look at instancing (one of the more powerful features of GL ). Instancing is one of the most important rendering techniques to learn as it'll push you further faster when it comes to what you can create.

#### Building a VJ System

Just like yesterday we're going to take the skills we've learned in learning how rendering works and start to think through building a mixer for realtime visuals. We won't get to add all the features we might want, but we'll get a good start.

#### Tracking Performers with a Kinect

Working with live sensors can be a little tricksy. In the afternoon we're going to pull apart what the Kinect sees, and how we can use that data. We're going to start with a simple representation of form, and from there we'll add some post process effects to build out a complete effect.

#### Q&A / Official Wrap

There's always more to cover than we have time - what are some of the missing pieces that we didn't cover? What do you want to learn next? What are some barriers you see to doing some development on your own? These last few official minutes are yours to choose what we talk about.

#### End of Day 2

I know you're all hungry for more programming, and so am I. I'm available for the next 2 hours to answer questions, look over work, help you do some programming, or talk through how to actualize a concept you've been thinking about. 

_documentation written in markdown_