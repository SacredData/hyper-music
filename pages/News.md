---
layout: profile
post_list: "date"
toc: false
home_btn: true
btn_text: true
footer: true
title: "News"
author: "Andrew Grathwohl"
encrypted_text: false
image: /img/bn.jpg
permalink: /news/
---
# News

## 1615051777056 (03/06/2021)
> Where we are going from here

After more than ten years, the Sonic Multiplicities code base has reached a
level of maturity where it is now feasible to begin generalizing the underlying
functions.

### New OSC Web Interface

We started off this process by constructing a web GUI for controlling SM
performances. This OSC controller can be utilized by anybody with a device
connected to the same LAN as the SM system. By generalizing the basic on/off
controls of the software, setup and instantiation is easier than ever before. It
also provides the added benefit of being a totally silent way to control the SM,
getting rid of the previous issues we had with foot pedals actually being picked
up by the SM analysis software during start-up.

Next, we have to address the SM seed data interface and the audio IO layers.

### Seed Data

SM performances are generally seeded with our purpose-built neural nets and a
combination of reliable metrics that could be acquired for free from the
internet. However, as time has progressed we have lost access to several of
these valuable resources.

Though we have always been able to substitute bad data for better data - even in
real time - these problems demonstrate the fallibility of our approach. We are
presented with the need for a better solution, because it will also generate
fantastic new creative avenues for our project.

Generalizing the SM data inputs will present new challenges in normalizing the
values provided, to retain musicality. It will also put us back into the
position where our neural nets will be challenged with totally new forms of
musical possibilities, expanding its own creative horizons.

### Audio I/O

More notably, this will open us up to new kinds of data being provided. Seeds
for SM have always been static values derived from the moment in time when the
performance begins. Now, seeds can be streamed and constantly changing, allowing
for new kinds of inputs such as from sensors.

Beyond the artistic possibilities, there are also exciting technical potentials
by making this move. The stability brought about by this work will enable the
software to be embedded within AudioUnits and VSTs so that people can attach an
SM environment to any audio application as an instrument plugins.
