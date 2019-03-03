# Strawberry Fields

## Introduction @unplugged

TODO INSERT GIF OF GAME

In this tutorial, you will build a simple game with the goal of collecting strawberries before time runs out. When a player eats a strawberry the score goes up. When a player eats a taco time power up the countdown restarts!

## Step 1 @fullscreen

Let's make the background more field like.  In ``||scene:Scene||`` section, drag  ``||scene:set background color to||`` in to the ``||loops:on start||`` block. Click inside the grey box to select a new background color. Let's make the color green.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
// @highlight
scene.setBackgroundColor(7)
```

## Step 2 @fullscreen

Without a player, there is no game. In the ``||sprites:Sprites||`` section, drag  ``||variables:set mySprite to||`` in to the ``||loops:on start||`` block **after** ``||scene:set background color to||`` block.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
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

## Step 3 @fullscreen

Choose your character! Click on the grey box in ``||variables:set mySprite to||`` block. If you're feeling artistic you can use the **Editor** to make you're own character. Alternatively pick a character from the **Gallery**.

TODO INSERT GIF

## Step 4 @fullscreen

Let's make the character move around the screen with arrow keys. From the ``||controller:Controller||`` section drag the ``||controller:move mySprite with buttons||`` to the end of the ``||loops:on start||`` block. 


```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
scene.setBackgroundColor(7)
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
// @highlight
controller.moveSprite(mySprite)
```
## Step 5 @fullscreen

Scores give the player a goal and a target to for them to improve upon. In the ``||info: Info ||`` section, drag ``||info: set score to ||`` block to the end of the ``||loops:on start||`` block.


```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
scene.setBackgroundColor(7)
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
controller.moveSprite(mySprite)
// @highlight
info.setScore(0)
```

## Step 6 @fullscreen

Urgency adds another level of challenge to a game. A countdown timer can add such a challenge. In the ``||info: Info ||`` section, drag the ``||info: start countdown ||`` to the end of the ``||loops:on start||`` block.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
scene.setBackgroundColor(7)
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
controller.moveSprite(mySprite)
info.setScore(0)
// @highlight
info.startCountdown(10)
```