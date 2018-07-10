---
layout: single
title:  "Learning Like Putty"
header:
  overlay_image: /assets/images/topomap.png
  caption: "Photo credit: Koba-chan [Public domain], from Wikimedia Commons created on Demis Map Server"
---

## How does machine learning work? An analogy.

Let's start with an analogy. Suppose you want to make a model of a complicated
surface, like a topographical map of the United States. One way would be to
make many detailed careful measurements, and create a set of blueprints for
recreating all the individual mountains and valleys on the map, then build your
model from those measurements. 

What you've created with your measurements is basically a set of detailed
instructions for recreating that specific map. If the map was swapped out with
another one, say a topographical map of Canada, your measurements would no
longer be helpful. 

What are the features of this approach?

* The new model is only as good as the measurements made, which could be prone
  to human error.
* The solution is labor intensive, since many painstaking measurements would be
  required.
* The solution is non-transferable: it won't work on a different problem, for
  example if we change the map, without basically starting over from scratch.

Now suppose instead that we made our model by pouring some kind of liquid putty
over the map and letting it harden. The putty is like a blank slate that
*learns* the contours of the map, without us directing it where to go. What is
directing the putty? In this case, just gravity, i.e. a fairly simple rule that
acts on the molecules of the putty.

Nevertheless, after the process, the putty now in some sense contains all of
the relevant information of the map. We've created a mold of the map that 
*knows* about all of the mountains and valleys and so on. 

What if the topographical map of the U.S. was swapped out for a map of Canada?
The procedure would need to be repeated, but the exact same substance (the
putty) can be used, and the steps are the same: let the putty flow over the map
and harden. 

What are the features of the putty approach?

* Depending on the properties of the putty, it could actually learn to make a
  better model (or a worse one) than a human measuring by hand.
* It requires little to no mental labor: the *learning* of the shape of the
  terrain is essentially a mechanical process governed by simple rules.
* The solution isn't specific to the input - we could learn one map or another
  using the same putty.

This is in many ways what machine learning and especially deep learning is all
about: you start with an extremely flexible model like the putty, that can take
on many different shapes. This might be a mathematical model with many
parameters that can be adjusted. An extremely promising model currently being
used for this purpose in all sorts of applications is the deep neural network.

Once you have your putty, you need some data that defines your problem. This is
like the original topographical map. The data has some shape that we want to
learn. The putty is allowed to change its shape, little by little, according to
some simple rules. While the actual putty changes and settles in a way that
minimizes the gravitational potential energy, the neural network parameters
change little by little to minimize some quantity you've chosen in advance,
such as an error function. By the end, the putty has learned the shape of the
map, or the neural network has learned the *shape* of the data. 

## Most problems are just topographical maps.

The beauty of this approach is that most problems can be reduced to this
problem of letting the putty learn to copy the topographical map. All data
lives in some mathematical space. For example, pictures of human faces can be
reduced to pixels, which can be reduced to a list of the colors of the pixels,
and those colors can be represented by numbers. So a picture of a human face is
a list of numbers. Viewing those numbers as coordinates, the human face becomes
a single point in the space of all possible images of a certain resolution. If
we want to learn to recognize human faces, we really just want to learn the
shape of the collection of all points in that larger space that actually
represent human faces.  We want to learn the topography of a certain landscape,
in other words. 

The [manifold hypothesis][manifold hypothesis] is the idea that real world data
sets (like pictures of faces) in practice often have a relatively simple shape,
out of all the possible shapes they could have in principle (not the shape of
faces, remember, but the shape of the set of all possible human faces). The
deep neural network is a flexible enough object that it can learn the mountains
and valleys of this shape, all the small idiosyncrasies. For many kinds of
data, this can already be done at levels of skill beyond what humans can do on
their own. 

So for example, if we wanted to write a computer program that recognized human
faces, we'd have to write code -- an explicit algorithm -- that described
everything we consciously know about human faces, the colors, the shapes, etc.
about how to tell if the picture we see is a face. This would be extremely
difficult and not very accurate. 

Even more so because when we recognizes a face, we likely can do it without
even thinking about it! We don't have to stop and think: does it have the
features and shapes and colors I expect? No, instead we just more or less
instantly realize it as a face. This is because our brains are like a giant
implementation of the putty: a real-life neural network that has already been
molded by our genes and our experience to learn the topographical map of human
face-space, inside the larger space of all images. If we can't consciously
express all of the rules by which we recognize faces, then we have no real hope
of writing those rules into an explicit algorithm. 

This is where machine learning comes in. Instead of trying to write out the
rules explicitly, i.e.  making explicit measurements of every mountain and
valley of the face-space, we just create a putty, the neural network, and allow
it to flow over some data. In this case, lots of pictures. In the end, we get a
model that can recognize a human face that works in much the same way (broadly
speaking) that our own brain recognizes a human face. With enough training data
and a big enough neural network, it could in principle learn to recognize faces
better and faster than a human brain. 

Here's an [example][celebrity faces] where some researches trained a neural
network to learn the manifold of celebrity faces. Then, since any point in that
space should correspond to a celebrity-like face, they can generate new faces
of non-real celebrities by picking random  points in that space!


Anyway, if you've read this far, you've got the basic idea of deep learning:
it's all about the putty.  

[manifold hypothesis]: https://stats.stackexchange.com/questions/66939/what-is-the-manifold-assumption-in-semi-supervised-learning
[celebrity faces]: https://www.youtube.com/watch?v=G06dEcZ-QTg
