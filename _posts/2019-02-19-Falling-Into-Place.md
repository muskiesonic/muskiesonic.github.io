---
layout: post
title: Falling Into Place
---

## Falling Down

I was able to add some motion to a Tetris piece. Currently it is falling with the classic Tetris stutter. No collision detection yet, so once it goes past the screen it's gone into the cornflower blue abyss until the next run.

Rotating the piece was accomplished by performing a transpose on the 2d short array holding the block positions. Since my naive approach to transpose only works for square matrices, I'll have to update the rest of the pieces to have a square shape. At least for now the T piece is falling and I can press space to start rotating to the right.

## User Input

To control the rotation, I've added some super basic user input detection. It's just looking to see if a couple keys are currently being pressed. It makes for some finicky controls but it'll do for now. Left and right controls are also included with the Tetris stutter since I was able to get the falling stutter to look good.

## Moar Pieces

Next I'm going to have to place with each of the pieces to make sure they fall and rotate correctly. Maybe after that I'll add some collision detection.

-Jayson