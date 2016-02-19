---
title: States
layout: documentation
css: /public/css/documentation.css
weight: 3
nav:
  prev:
    label: Interactions
    path: Interactions
  next:
    label: Animations
    path: Animations
---

Every prototype has multiple states it can transition between. Origami has several patches to help you manage these states.

## State patches

  <ul class="bulleted-list">
    <li>
      [Switch &rarr;](../patches/Switch.html) <span class="key modifier inline">&#8679;</span><span class="key letter inline">S</span>
      <br>
      The Switch patch works like a light switch. Flipping it when it's on will turn it off, and when it's off flipping it will turn it on. Switches help you build simple two-state interactions. For example you might have a Switch managing whether a photo is full screen or not or whether a modal view is on screen.
      <br>
      <ul class="patch-chain">
        <li>
          <div class="patch-block">
            <div class="patch producer">
              <h3>Interaction 2</h3>
              <ul class="inputs">
                <li>Enable</li>
              </ul>
              <ul class="outputs">
                <li>Down</li>
                <li>Up</li>
                <li>Tap</li>
                <li>Drag</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch processor">
              <h3>Switch</h3>
              <ul class="inputs">
                <li>Flip <span class="patch-value">&#10003;</span></li>
                <li>Turn On</li>
                <li>Turn Off</li>
              </ul>
              <ul class="outputs">
                <li>On / Off</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch consumer">
              <h3>Layer</h3>
              <ul class="inputs">
                <li>Enable <span class="patch-value">&#10003;</span></li>
              </ul>
              <hr>
            </div>
          </div>
        </li>
      </ul>
      <br>
    </li>
    <li>
      [Index Switch &rarr;](../patches/Index-Switch.html)
      <br>
      Index Switch patches are useful for mutually exclusive states that cannot coexist, e.g. a tab bar.
      <br><br>
      Index Switches are commonly used with [Multiplexers](../patches/Multiplexer.html) to pass different values depending the state. For example, if you wanted to change a navigation bar title between 3 states:
      <ul class="patch-chain">
        <li>
          <div class="patch-block">
            <div class="patch processor">
              <h3>Index Switch</h3>
              <ul class="inputs">
                <li>Input 0 <span class="patch-value">&#10003;</span></li>
                <li>Input 1</li>
                <li>Input 2</li>
              </ul>
              <ul class="outputs">
                <li>Index</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch processor">
              <h3>Multiplexer</h3>
              <ul class="inputs">
                <li>Source Index <span class="patch-value">0</span></li>
                <li>Source #0 <span class="patch-value">News Feed</span></li>
                <li>Source #1 <span class="patch-value">Notifications</span></li>
                <li>Source #2 <span class="patch-value">Profile</span></li>
              </ul>
              <ul class="outputs">
                <li>Output</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch consumer">
              <h3>Text Layer</h3>
              <ul class="inputs">
                <li>Text <span class="patch-value">News Feed</span></li>
              </ul>
              <hr>
            </div>
          </div>
        </li>
      </ul>
    </li>
    <li>
      [Counter 2 &rarr;](../patches/Counter-2.html)
      <br>
      Counter patches are useful for mutually exclusive states that cannot coexist, and increment in a fixed order e.g. an onboarding flow.
      <ul class="patch-chain">
        <li>
          <div class="patch-block">
            <div class="patch producer">
              <h3>Counter 2</h3>
              <ul class="inputs">
                <li>Increase</li>
                <li>Decrease</li>
                <li>Maximum Count <span class="patch-value">2</span></li>
              </ul>
              <ul class="outputs">
                <li>Number</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch processor">
              <h3>Multiplexer</h3>
              <ul class="inputs">
                <li>Source Index <span class="patch-value">2</span></li>
                <li>Source #0 <span class="patch-value">Enter information</span></li>
                <li>Source #1 <span class="patch-value">Verify email</span></li>
                <li>Source #2 <span class="patch-value">Finished!</span></li>
              </ul>
              <ul class="outputs">
                <li>Output</li>
                <div class="cable"></div>
              </ul>
              <hr>
            </div>
          </div>
        </li>
        <li>
          <div class="patch-block">
            <div class="patch consumer">
              <h3>Text Layer</h3>
              <ul class="inputs">
                <li>Text <span class="patch-value">Finished!</span></li>
              </ul>
              <hr>
            </div>
          </div>
        </li>
      </ul>
    </li>
  </ul>


## Index numbers represent states
Both Switch and Index Switch patches output a number for the state that is active. Switch patches output a 0 (off) or a 1 (on), and Index Switch patches output a number starting from 0 for the first state, to 1 for the 2nd, and so on:

<ul class="bulleted-list">
  <li>Index 0 &rarr; Initial state / Off State</li>
  <li>Index 1 &rarr; 2nd state / On State</li>
  <li>Index 2 &rarr; 3rd state</li>
  <li>Index 3 &rarr; 4th state</li>
  <li>...</li>
</ul>