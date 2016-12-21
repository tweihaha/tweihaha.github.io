---
layout: page
title: Rolling Pong
permalink: projects/rollingpong/
subtitle: Rolling Pong
---

Imagine that you are balancing a **ping pong ball** on a surface. 
You have to stop the ball at certain points in order to score.
Controlling the ball is already a difficult task.
Unfortunately, your naughty friends are trying to keep you from scoring!

What should you do?

### Meet Rolling Pong

<img width="60%" src="/assets/img/rollingpong/rollingpong.png">

It is a real-time multiplayer mobile game built on iOS. You can connect your device with your friends' via WiFi or Bluetooth. There can be at most four players.
Every player has to control the ball by tilting his/her device. In the given time, players have to find the scoring point on the map as well as stop their friends from scoring. 
When the time is up, the player who gets the highest score wins the game.

Let's watch a demo video.

<iframe width="560" height="315" src="https://www.youtube.com/embed/HF_a7jmzgYc" frameborder="0" allowfullscreen></iframe>

In addition to the multiplayer mode, we also create some **single-player stages**.
There are three types of stages, Fire Pong, Pac Pong, and Boss Pong.

{::nomarkdown} 
<div style="overflow: auto;">
    <p><img style="float: left;" width="20%" src="/assets/img/rollingpong/firepong.png"></p>
    <h4>Fire Pong Stage</h4>
    <p>In the <strong>Fire Pong Stage</strong>, you are a ball on fire, so you have to find the "H," "2," and "O" on the map to extinguish the fire. However, the path you've been through will also be on fire, so you cannot step on it again. In order to win the game, you have to find H2O before the time is up without stepping on any point through which you've been.</p>
</div>

<div style="overflow: auto;">
    <img style="float: left;" width="20%" src="/assets/img/rollingpong/pacpong.png">
    <h4>Pac Pong Stage</h4>
    <p>The <strong>Pac Pong Stage</strong> is just like the rolling-pong version of Pac Man. You have to collect all the stars on the map without being caught by the ghosts to win the stage.</p>
</div>

<div style="overflow: auto;">
    <img style="float: left;" width="20%" src="/assets/img/rollingpong/bosspong.png">
    <h4>Boss Pong Stage</h4>
    <p>In the <strong>Boss Pong Stage</strong> you are fighting against an artificial intelligent player. Defeat the AI to win this stage!</p>
</div>
{:/}

### Technical Issues

- This game is powered by [SpriteKit Framework](https://developer.apple.com/reference/spritekit) of iOS, and the code was written in Objective-C.
- It can connect to players' Facebook accounts.
- We built a cloud database on [Parse](https://parse.com/).
- Since it is a real-time game, the data transmission between devices must be extremely fast. Thus, we developed self-made protocols and data packets to meet this demand.
- The AI Pong can predict the optimal path so that it can pass through the obstacles.

<img style="float: right;" width="60px" src="/assets/img/rollingpong/bitmap.png">

- The maps are created using a technique called **bitmap transformation**. We generate an image, and each pixel on the image represents a particular item that will be placed on the map. We use different colors for computers to distinguish among various kinds of items. (Like the figure on the right.)

