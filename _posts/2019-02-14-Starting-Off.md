---
layout: post
title: Starting Off
---

## New Project

Starting off on my journey of recreating Tetris, I need a couple things. I'm currently developing on a Macbook Pro. Since I'm planning on using MonoGame, I plan to grab Visual Studio for Mac. I can download the MonoGame extension to get the Visual Studio project templates and MonoGame SDK installed easily.

I've already created a repository on GitHub that I can use to store all of my project files. I'm going to start by cloning the project locally, creating a new cross platform project and just try to get the base project to compile and run.

__Startup software:__

* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/)
* [MonoGame 3.7.1](http://community.monogame.net/t/monogame-3-7-1-release/11173)

## Initial Compile

Right off the bat, I've found that the MonoGame project template for cross platform projects is a bit busted. I was able to fix it easily by modifying the solution options.

Once I've modified the build configuration mappings under the solution options, I was able to compile the project and see the very pretty cornflower blue screen.

![First Compile](/images/first_compile.png, "First Compile")

Hurray, it's a working game! It's just missing the fun parts.

## First Steps

The first thing I did after successfully compiling was to generate pieces. I did it rather quickly and poorly, but they show up on the screen and we can always come back to clean them up. Right?

![First Pieces](/images/first_pieces.png, "First Pieces")

```C#
using System;
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;

namespace mono_tetris.Desktop
{
    public class Tetromino
    {
        public static short HEIGHT = 16;
        public static short WIDTH = 16;

        public static Tetromino Square(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {1, 1},
                {1, 1}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino I(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {1},
                {1},
                {1},
                {1}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino Z(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {1, 1, 0},
                {0, 1, 1}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino S(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {0, 1, 1},
                {1, 1, 0}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino T(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {1, 1, 1},
                {0, 1, 0}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino L(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {1, 0},
                {1, 0},
                {1, 1}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public static Tetromino BackwardsL(Texture2D texture, Vector2 postion)
        {
            var blocks = new short[,]
            {
                {0, 1},
                {0, 1},
                {1, 1}
            };
            return new Tetromino(texture, postion, blocks);
        }

        public Tetromino(Texture2D texture, Vector2 position, short[,] blocks)
        {
            Texture = texture;
            Position = position;
            Blocks = blocks;
        }

        public Texture2D Texture { get; set; }

        public Vector2 Position { get; set; }

        public short[,] Blocks { get; }

        public void Draw(SpriteBatch spriteBatch)
        {
            for (var i = 0; i < Blocks.GetLength(0); i++)
                for (var j = 0; j < Blocks.GetLength(1); j++)
                    if (Blocks[i, j] == 1)
                        spriteBatch.Draw(Texture, new Vector2(Position.X + (j * WIDTH), Position.Y + (i * HEIGHT)), Color.White);
        }
    }
}

```

## Up Next

Next, I want to focus on getting the pieces to spin, hopefully then I can get a better idea for how some of the Tetromino class should be laid out.

-Jayson