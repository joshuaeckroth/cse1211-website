---
layout: post
title: Group project 2, part 1
due: Nov 25, 11:59pm
---

# Group project 2, part 1

The second group project will be split into two parts:

- Part 1, due Nov 25 (described here)

- Part 2, project presentations on Dec 5 (10:00am - 11:45am)

For part 1, you must have provide:

- A description of your game, and your goals for part 2.

- The first "level" of your game, with basic keyboard or mouse
  control.

## Description and goals for part 2

You must provide, in part 1, a description of your game and goals for
part 2. For example:

> "Pong" is a two-player game where each player tries to reflect a
> ball back to the other player by moving a paddle. The player who
> wins a round is the one who never fails to reflect the ball. Greater
> skill requires predicting where to move the paddle to reflect the
> ball. Player 1 is controlled by the keyboard, Player 2 is controlled
> by the mouse. The paddles are fixed at the left and right sides of
> the screen but can be moved up and down. The ball's initial velocity
> is random.
>
> This first version of the game only has the basic gameplay. Part 2
> will include increased difficulty (faster ball movement), an opening
> screen and win/loss screen, a high score list, and better graphics.

Separately, on Dropbox, turn in the ZIP archive of your game and a
text/Word/PDF document of your description and goals.

## Requirements for the game

Your final game should be the culmination of all that you have learned
in this class. There is one exception: you are not required to use
fisica.

Your code is required to include:

- At least two classes in addition to your main file.

- At least one use each of `pushMatrix()` and `popMatrix()`, and at
  least one use of either (or all of) `scale()`, `rotate()`, and
  `translate()`.
  
- At least one use of `PImage` and `loadImage()`.

- At least one use of an array.

- Mouse input or keyboard input (or both).

Additionally, you are required to have:

- An attractive background image or design.

- An opening screen that gives instructions for how to play.

- At least three levels of difficulty. The player(s) may or may not be
  allowed to choose the difficulty level.

- A way to restart after losing.

- A list of scores, listed in the order they were obtained (most
  recent first). This is not a "high score" list because it does not
  have player names and all scores are kept (not just the
  highest). For space reasons, display only the most recent 5 or 10
  scores (you choose how many). Show this screen when the player loses
  (or wins). You might find the `expand()` and `shorten()` functions
  from the
  [array utilities](/videos/2013-09-27-array-utilities.html)
  video to be helpful.
  
