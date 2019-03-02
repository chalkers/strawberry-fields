# Strawberry Fields

## Introduction @unplugged

In this tutorial, you will build a simple game with the goal of collecting strawberries before time runs out. When a player eats a strawberry the score goes up. When a player eats a taco time power up the countdown restarts!

## Step 1 @fullscreen

Let's make the background more field like.  In ``||scene:Scene||`` section, drag  ``||scene:set background color to||`` in to the ``||loops:on start||`` block. Click inside the grey box to select a new background color. Let's make the color green.

```blocks
// @highlight
scene.setBackgroundColor(7)
```

## Step 2 @fullscreen

Without a player, there is no game. In the ``||sprites:Sprites||`` section, drag  ``||variables:set mySprite to||`` in to the ``||loops:on start||`` block **after** ``||scene:set background color to||`` block.

```blocks
scene.setBackgroundColor(7)
// @highlight
mySprite = sprites.create(img`
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
. . . . . . . . . . . . . . . . 
`, SpriteKind.Player)
```
