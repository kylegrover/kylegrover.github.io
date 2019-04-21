---
category: Code Art
tags:
- GLSL
- Synesthesia
- Beginner
background: Default
title: Adding a Slider to a Scene in Synesthesia
background_color: ''
background_image: ''
background_glsl: ''
date: 2019-04-20 18:41:46 +0000
layout: post

---
So you've downloaded <a href="http://synesthesia.live/" target="_blank">Synesthesia</a>, you're playing around with the scenes and having fun, but you want to control something and the slider just isn't there. Maybe you want to control the speed of an effect, or more control over the audio reactivity, I see a lot of people asking questions about Synesthesia scenes that ultimately boil down to needing this skill, so I figured I'd type it out real nice one time to share again and again.

This guide aims to take an absolute beginner through all the steps needed without requiring or diving into the fundamentals of coding, GLSL, JS, or JSON, but those are all great fundamentals you'll want to learn at some point. If you'd like to build your understanding of GLSL Code Art I highly recommend the free online <a href="https://thebookofshaders.com/" target="_blank">Book of Shaders</a> and of course <a href="https://www.synesthesia.live/docs/index.html" target="_blank">Synesthesia's Official Docs</a>.

## A Quick Overview of the Process

I'm going to break this down into two basic steps: first we'll create a slider, then we'll modify the code so our slider modifies something. Once you're comfortable with that it's just rinse and repeat until something cool happens.

But before we start editing files let's take a step back and look at how a scene is structured and how the program reads it. Synesthesia scenes have 4 main files, each in a different format:

* **main.glsl:** graphics processing code lives here
* **scene.json:** settings are written here in JSON (I'll talk more about JSON below)
* **script.js***: an _optional_ file that allows you to do some extra processing in JavaScript before each frame runs
* **some_name.png/jpg**: the scene thumbnail, as listed in the scene.json file

_Note: Synesthesia Scenes can also include any number of additional images to read from within your GLSL code._

Thankfully we only need to work with 2 or 3 of those files, depending on the scene. First we'll focus on the most common scenario where we're only editing the GLSL file and the JSON file, after that we'll deal with the JavaScript file.

## Adding a Slider to the Scene

Let's start out by adding our own slider to the control panel. It won't do anything yet, but it's a good place to start. I'll be working with the default scene Glassier if you'd like to work along.

1. If you don't have a scene ready to edit, choose one from the library view and click the "duplicate scene" button indicated by two documents, then find that new scene (ie "Glassier_dup") and click the "edit scene" button indicated by a pencil.
2. You should be greeted by the scenes folder. Open the file "scene.json" in your <a href="https://mikkegoes.com/finding-the-best-text-editor-for-coding/" target="_blank">favorite code editor</a> (it may appear as just "scene" depending on your OS preferences)
3. Note all the existing settings, and the format they're written in. Try to figure out what they're doing. If you're editing Glassier like I am, note that it's made by the fantastic <a href="https://www.shadertoy.com/user/Flexi" target="_blank">Felix Woitzel</a>.
4. Find the section wrapped in `_"CONTROLS"_`` : [ ... ]` and add this after the `[` but before the next `{`

       {
         "NAME": "my_new_slider",
         "TYPE": "slider",
         "UI_GROUP": "my custom controls",
         "DEFAULT": 0,
         "MAX": 1,
         "MIN": 0,
         "DESCRIPTION": "This controls whatever I want it to!"
       },
5. Save the file and reload your scene in Synesthesia. If you did everything right, you should see your slider show up in the control panel. It won't do anything yet, but we're getting somewhere! If you see loads of red text in the Console Output at bottom right, you probably goofed up your syntax, as I expertly demonstrate in the screenshot below. Code editors with color highlighting are your best friend for spotting these types of errors.

![](https://res.cloudinary.com/kylegrover/image/upload/./v1555781631/goofed-up-json-syntax-synesthesia.png){: .align-center }

## Connecting Your Slider to a GLSL Variable

Okay, we have our very own slider - rad. The configurations you added to your scene.json file created a slider that goes from 0 at the bottom to 1 at the top, and we can access that number with the variable name `my_new_slider`. Now, how do we make it do something?

Put simply, we're going to use our variable to modify another variable. Every bit of information in a shader is stored as a variable. All of these variables serve to drive functions and logic that ultimately output each pixel's color values each frame. We're going to: choose a variable to manipulate, choose a way to manipulate it, and then test it out!

#### Choosing a Variable or Number

Your options here are truly limitless, but to avoid diving into the specifics of how one shader works I'll play with something that's relevant to every scene: color. If you don't know what you want to modify, just pick a random variable or number and see what happens when you modify it! If you do have a specific idea in mind, you might luck out by searching for a relevant variable name or exploring <a href="https://www.synesthesia.live/docs/uniforms/index.html" target="_blank">Synesthesia's built in "Uniforms"</a>, but you might need to spend a while getting know the code before you find that magic variable.

I'm going to bypass all of that for now by jumping right to the end of the GLSL file and finding the final `return` line - for Glassier that was line 783: `return fragColor;`. This line says "okay, we're done here, set the current pixel to this RGBA color". The variable I'll be modifying is fragColor, or more specifically fragColor.r - the red value.

#### Choosing an Operator

Now we have two variables, our custom slider that goes from 0 to 1, and our chosen variable - mine is a red channel value that also ranges from 0 to 1. All that's left is to choose what to do with these numbers, and again your options are as endless as the field of mathematics, but let's try two basic examples - multiplying, overriding - and then one weirder example.

**Multiplying**: this one's simple, I'll just add this line before the return line: `fragColor.r *= my_new_slider;` In english: Take the current red channel value and multiply it by my slider value. With this saved, the slider has no effect when it's at the top, and at the bottom it removes the red entirely. Here's how it looks around 0.3:

![](https://res.cloudinary.com/kylegrover/image/upload/./v1555785135/glassier-slider-red-times-equals.png){: .align-wide }

Not bad, one line of code gives us a new color scheme!

**Overriding**: even easier, instead of `*=` we'll just use `=`. When the slider's at the bottom this will look just like when we multiplied - no red - but as you dial it up it'll add a flat red tinge to everything:

![](https://res.cloudinary.com/kylegrover/image/upload/./v1555785568/glassier-slider-red-override.png){: .align-wide }

**Weird Stuff**: Let's branch out. What if we raise the red value to the power of the slider, or vice versa? How about if we wrap it in a modulo operator? Let's try both with `fragColor.r = mod(pow(my_new_slider, fragColor.r), 0.1) * 10.0;`

![](https://res.cloudinary.com/kylegrover/image/upload/./v1555784909/glassier-slider-red-mod-pow.png){: .align-wide }

Wicked! And there's no end to the depth of control you can configure. In that line above I included a few hard-coded numbers, `0.1` and `10.0` - those could both also be sliders instead.

### The End, For Now

This post has really grown beyond my initial plans and I'm going to call it for now and post what I have online. Hopefully this helps someone out, check back in for an updated version where I tackle the scripts.js file as well as a few tips for smoothly modifying your time variables.


{% comment %}

## Connecting Your Slider to a JS Variable

* gloss over a lot of the general stuff we already covered, just pinpoint an easy example (glassier has no js, maybe try a 3d scene)

#### Some Notes on JS Classes/Objects & GLSL Variables in Synesthesia

* explain how to build a js class/object, and how synesthesia passes that data to the GLSL loop

#### Smoothly Modifying Time Variables using JS

* use thresholder for reference

{% endcomment %}