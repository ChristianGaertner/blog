+++
date = "2016-05-07T18:33:56+02:00"
draft = false
title = "Climbing Wall Timekeeping Project 00"

+++

>_TL;DR_ We want to build a timekeeping (just a fancy way of saying 'some stopwatches') system for a local climbing wall.


Let me start this very first blog post on this series by explaining how it all started and what I am trying to achieve, this post will not cover any technical aspects about the build, rather it introduces you to the project, my ideas and thoughts. The next one will be the very first _real_ post on this topic, hence the number _00_ as index for this post.

A few friends of mine are running a climbing wall in our district and I tend join them occasionally for some climbing. The wall is about 25m tall and has 4 seperate lanes (2m each), all are parallel to each other and very straight since it's located on one wall of the steeple here. One day we were joking around how nice it would be to have some buzzers on the top of the climbing wall to compare the results, you know... guys seem to like comparing their... track times, of course! After some joking around, I realized that this would make a great project for a few weekend to tinker around with. I liked the idea of building an Arduino based project for quite some time now and this seems like the perfect opportunity.


I'd like to start the technical side of this project with a small disclaimer. I am a software developer. I have some practical experience with electronics, but mainly hooking up a few transitors and LEDs, etc. I have not touched an Arduino myself, yet. But I've watched a lot of projects videos on YouTube, not for learning, but mostly because I like watching somebody build it.[^1]

## The Plan

So what have I planned? Good question. Not very much yet seems to be the answer right now - sadly.

But here is the basic outline. I try to describe the interesting things in more detailed blog posts, as I go along in this project. This __won't__ be a tutorial! I want to make this clear, however it __will__ be (hopefully) a progress report and note taking along side. Two reasons. I have an excuse to host my own blog[^2] and force myself to keep up with the project and not let it fade into oblivion.

We want to mount 4 buzzers (fancy switches) to the top of the climbing wall, these should be used to stop the timer for the given lane. The timer should be started from a central up at the ground, where the timer display itself lives.

The display itself will be a 1.8" Color TFT[^3] display inside a waterproof enclosure (the Arduino will live here to). I will be using an Arduino Micro Pro. I am aware that an Uno might be easier to get started with, but money is an important factor since I do not want to spend that much for a side project like this.

### Considerations

25m is a long distance, and a cable this long is basically a giant antenna which will pick up a lot of noise. This might interfere with an acurate time measurement. So I tought - we will see how this idea holds - a CAT-6 LAN cable should do the trick, in conjunction with the button pin on the arduino pulled _HIGH_.

### UI Design
The screen is rather small and a good UI/UX are crucial if the device will be used during normal operation of the climbing wall. If it is too complicated nobody will use it!

The project box will expose a total of 3 buttons. Two directly below the screen and a bigger one somewhere else. The bigger one will act as start button while the other two as soft buttons.[^4] This allows for more complex interactions in the future.

The screen will be dominated by a large clock, the most important aspect of every stopwatch, I guess. If one presses start the clock should be counting up, until all 4 buttons on top of the lanes have been pressed.
As soon as the first one reached the top the time should be recorded and displayed in a smaller font face below the main clock. This acts as basic ranking system for each given run.

## Final Thoughts

Everything else will be figured out as I go along with this project. Tonight I will start by tinkering around with the arduino, lighting up some LEDs and pressing some buttons. This should be fun.

The next post in this series will likely cover the development of the UI for the TFT display, or about my solution for acurate time keeping and how to handle noise on the input channel. As I said, this is not a tutorial, it is a project journal.



[^1]: I like the YouTube Channel [GreatScott](https://www.youtube.com/user/greatscottlab)
[^2]: I hope that I will write more posts, if I have system already up and running...
[^3]: I got this [one](https://www.adafruit.com/products/358), which also has a built in SD card reader for persiting the times.
[^4]: the buttons will provide different functionality based on the screen menu.