---
layout: post
title: Collisions
---

## Collision Detection

Adding collsion detection tripped me up for a minute. I started by trying to create a Collision Detection class that would handle intersections between the gameboard and falling piece. This caused unnecessary complexity since I'm not creating a full fledged engine, especially for a specific game like Tetris.

Once I figured out that a simpler way might be better, I moved to a check/move style. When the user interaction causes a movement or rotation of the current piece, I check the parent gameboard state for collisions. If there are none, I keep the new position or rotation. If the new orientation intersects with the board walls or floor, the movement is reverted.

The check/move style collision detection makes the logic significantly simpler.

## Wall Kicks

As I was looking into how pieces should move in Tetris, I found guidelines for how the rulesets should be set up for a game to officially be called Tetris. I looked at some of the rotation logic to improve how rotating along the wall handles and I stumbled upon wall kicks.

[Tetris Rotation](https://tetris.wiki/SRS)

When rotating a piece, it's frustrating to be along the wall and stuck in a current rotation. The wall kick checks a couple of specific places a piece can be moved into so that the rotation works.

I was able to implement right handed wall kicks for the T shape. So I consider this a success. When I move the current piece around, the game has a decent feel. It still needs work but it's already feeling like Tetris.

-Jayson