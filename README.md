# Strawberry Fields

## Introduction @unplugged

TODO INSERT GIF OF GAME

In this tutorial, you will build a simple game with the goal of collecting strawberries before time runs out. When a player eats a strawberry the score goes up.

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

Scores give the player a goal and a target to for them to improve upon. 

In the ``||info: Info ||`` section, drag ``||info: set score to ||`` block to the end of the ``||loops:on start||`` block.


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

Urgency adds another level of challenge to a game. A countdown timer can add such a challenge. 

In the ``||info: Info ||`` section, drag the ``||info: start countdown ||`` to the end of the ``||loops:on start||`` block.

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

## Step 7 @fullscreen

Our game needs collectibles to be complete. In the ``||game: Game ||`` section, drag the ``||game: on game update every ||`` in to the coding area.

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
info.startCountdown(10)

// @highlight
game.onUpdateInterval(500, function () {
	
})
```

## Step 8 @fullscreen

We'll make a strawberry appear every second (1000 miliseconds). Change `500` to `1000` in the ``||game: on game update every ||`` block.

```blocks
// @highlight
game.onUpdateInterval(1000, function () {
	
})
```

## Step 9 @fullscreen

In ``||sprites: Sprites||`` section, drag the ``||variables:set mySprite2 to||`` block inside the ``||game: on game update every ||`` block.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let mySprite2: Sprite = null
game.onUpdateInterval(1000, function () {
	// @highlight
   mySprite2 = sprites.create(img`
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
})
```

## Step 10 @fullscreen

Instead of using the variable name of ``||variables: mySprite2||``, let's create a new one ``||variables: item||``. Click on the dropdown and click on ``||variables: New variable... ||``. Enter **item** in to the dialog box and press ``|Ok|``.

TODO INSERT


## Step 11 @fullscreen

Change the ``||sprites: sprite||`` inside the ``||variables: set item to||`` block to the strawberry sprite in the **Gallery**.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    // @highlight
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Player)
})
```

## Step 12 @fullscreen

The strawberry ``||sprites: sprite||`` needs to be ``||sprites: of kind||`` ``||sprites: Food||``. You can select ``||sprites: Food||`` from the drop down menu next to ``||sprites: Player||``.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    // @highlight
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
})
```

## Step 13 @fullscreen

We have a problem, our strawberry is appearing on top of the player sprite. Drag ``||sprites: set mySprite position to||`` the ``||game: on game update every||``. Change ``||variables: mySprite||`` to ``||variables: item||`` in the drop down menu.


```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    // @highlight
    item.setPosition(0, 0)
})
```
## Step 14 @fullscreen

In the math ``||math: Math ||`` section, drag one ``||math: pick random||`` block in to the ``||sprites: x||`` and another ``||math: pick random||`` block in to ``||sprites: y||``.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    // @highlight
    item.setPosition(Math.randomRange(0, 10), Math.randomRange(0, 10))
})
```

## Step 15 @fullscreen

All the strawberries are in the top left hand corner. By changing the values in the ``||math: pick random||`` blocks we can get a wider range of positions for each strawberry appearing every second.

In the ``||math: pick random||`` block in the ``||sprites: x||`` change the values from 0 and 10 **to** 10 and 150.  

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    // @highlight
    item.setPosition(Math.randomRange(10, 150), Math.randomRange(0, 10))
})
```

## Step 16 @fullscreen

In the ``||math: pick random||`` block in the ``||sprites: y||`` change the values from 0 and 10 **to** 10 and 110.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    // @highlight
    item.setPosition(Math.randomRange(10, 150), Math.randomRange(10, 110))
})
```
## Step 17 @fullscreen

When the player moves around and touches the strawberries nothing happens. We need to test if the player overlaps or collides with another sprite.

In the ``||sprites: Sprites||`` section, drag the ``||sprites: on sprite of kind Player overlaps otherSprite of kind Player||`` block in to the coding area.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Player, function (sprite, otherSprite) {
	
})
```

## Step 18 @fullscreen

When a ``||variables: sprite ||`` touches another sprite, ``||variables: otherSprite||``, and it's the correct kind the code gets executed.

Currenlty the other ``||variables: otherSprite||`` is set to kind ``||sprites: Player||``. This need to be ``||sprites: Food||`` to match the strawberry sprite type.


```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	
})
```

## Step 19 @fullscreen

When the player ```||variables: sprite||`` touches the strawberry ``||variables: otherSprite||`` we want the score to increment by 1 and for the strawberry to disappear.

In the ``||info: Info||`` section, drag the ``||info: change score by ||`` block in to the overlay block.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    // @highlight
    info.changeScoreBy(1)
})
```

## Step 20 @fullscreen

Moving the player over each strawberry now increments the score but it doesn't disappear. We need to **DESTROY** it!

Head over to the ``||sprites: Sprites||`` section, and find the ``||sprites: destroy ||`` block and drag it in to the ``||sprites: overlay||`` block. Drag the ``||variables: otherSprite||`` bubble over the ``||variables: mySprite||`` bubble.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    // @highlight
    otherSprite.destroy()
})
```
## Step 21 @unplugged

The basic game is complete! **Congratulations!** You can ``|Exit tutorial|`` and share the project with friends or even ``|Download|`` the game for compatible hardware!

Instead of exiting, you also have the option to make the game more complex by adding a Taco power up and adding obstacles.

## Step 22 @fullscreen

Let's add a taco **POWER UP**! That when it's collected it the countdown restarts.

Right click on the ``||game: on game update every ||`` block and click **Duplicate**.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
// @highlight
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 23 @fullscreen

We're going to have the taco power up to appear every 9 seconds. Change the value from 1000 to 9000 miliseconds (ms) in the second ``||game: on game update every ||`` block.


```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
// @highlight
game.onUpdateInterval(9000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 24 @fullscreen

It's good practice to change the names of sprites that do different things. Let's change the name (variable) from item to ``||variables: moreTime||``.

In the second ``||game: on game update every ||`` block, within the ``||variables: set item to||`` block, click on the ``||variables: item||`` dropdown and click on ``||variables: New variable...||`` and give it a new name **moreTime**.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let item: Sprite = null
let moreTime: Sprite = null
game.onUpdateInterval(1000, function () {
    item = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
game.onUpdateInterval(9000, function () {
    // @highlight
    moreTime = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    item.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 25 @fullscreen

We also need to update the ``||sprites: set item position to||`` block to have the new variable name of ``||variables: moreTime||``.

In the ``||sprites: set item position to||`` click on the ``||variables: item ||`` dropdown and select ``||variables: moreTime||``.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let moreTime: Sprite = null
game.onUpdateInterval(9000, function () {
    moreTime = sprites.create(img`
        . . . . . . . 6 . . . . . . . .
        . . . . . . 8 6 6 . . . 6 8 . .
        . . . e e e 8 8 6 6 . 6 7 8 . .
        . . e 2 2 2 2 e 8 6 6 7 6 . . .
        . e 2 2 4 4 2 7 7 7 7 7 8 6 . .
        . e 2 4 4 2 6 7 7 7 6 7 6 8 8 .
        e 2 4 5 2 2 6 7 7 6 2 7 7 6 . .
        e 2 4 4 2 2 6 7 6 2 2 6 7 7 6 .
        e 2 4 2 2 2 6 6 2 2 2 e 7 7 6 .
        e 2 4 2 2 4 2 2 2 4 2 2 e 7 6 .
        e 2 4 2 2 2 2 2 2 2 2 2 e c 6 .
        e 2 2 2 2 2 2 2 4 e 2 e e c . .
        e e 2 e 2 2 4 2 2 e e e c . . .
        e e e e 2 e 2 2 e e e c . . . .
        e e e 2 e e c e c c c . . . . .
        . c c c c c c c . . . . . . . .
    `, SpriteKind.Food)
    // @highlight
    moreTime.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 26 @fullscreen

It's taco time. The ``||variables: moreTime||`` looks like a strawberry!

Change the ``||sprites: sprite||`` to the taco from the **Gallery** from the sprite editor.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile
}
let moreTime: Sprite = null
game.onUpdateInterval(9000, function () {
    // @highlight
    moreTime = sprites.create(img`
        . . . . . . . e e e e . . . . .
        . . . . . e e 4 5 5 5 e e . . .
        . . . . e 4 5 6 2 2 7 6 6 e . .
        . . . e 5 6 6 7 2 2 6 4 4 4 e .
        . . e 5 2 2 7 6 6 4 5 5 5 5 4 .
        . e 5 6 2 2 8 8 5 5 5 5 5 4 5 4
        . e 5 6 7 7 8 5 4 5 4 5 5 5 5 4
        e 4 5 8 6 6 5 5 5 5 5 5 4 5 5 4
        e 5 c e 8 5 5 5 4 5 5 5 5 5 5 4
        e 5 c c e 5 4 5 5 5 4 5 5 5 e .
        e 5 c c 5 5 5 5 5 5 5 5 4 e . .
        e 5 e c 5 4 5 4 5 5 5 e e . . .
        e 5 e e 5 5 5 5 5 4 e . . . . .
        4 5 4 e 5 5 5 5 e e . . . . . .
        . 4 5 4 5 5 4 e . . . . . . . .
        . . 4 4 e e e . . . . . . . . .
    `, SpriteKind.Food)
    moreTime.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 27 @fullscreen

While a taco in real life is ``||sprites: Food||``, in our game it's a ``||sprites: PowerUp||``. By having a new kind of sprite it allows us to detect when our player overlays with the taco and run different code - to reset the countdown.

In the ``||variables: set moreTime to||`` block, click the ``||sprites: Food||`` dropdown and click ``||sprites: Add a new kind...||``. Enter **PowerUp** in the dialog box and click ``|OK|``.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile,
    PowerUp
}
let moreTime: Sprite = null
game.onUpdateInterval(9000, function () {
    // @highlight
    moreTime = sprites.create(img`
        . . . . . . . e e e e . . . . .
        . . . . . e e 4 5 5 5 e e . . .
        . . . . e 4 5 6 2 2 7 6 6 e . .
        . . . e 5 6 6 7 2 2 6 4 4 4 e .
        . . e 5 2 2 7 6 6 4 5 5 5 5 4 .
        . e 5 6 2 2 8 8 5 5 5 5 5 4 5 4
        . e 5 6 7 7 8 5 4 5 4 5 5 5 5 4
        e 4 5 8 6 6 5 5 5 5 5 5 4 5 5 4
        e 5 c e 8 5 5 5 4 5 5 5 5 5 5 4
        e 5 c c e 5 4 5 5 5 4 5 5 5 e .
        e 5 c c 5 5 5 5 5 5 5 5 4 e . .
        e 5 e c 5 4 5 4 5 5 5 e e . . .
        e 5 e e 5 5 5 5 5 4 e . . . . .
        4 5 4 e 5 5 5 5 e e . . . . . .
        . 4 5 4 5 5 4 e . . . . . . . .
        . . 4 4 e e e . . . . . . . . .
    `, SpriteKind.PowerUp)
    moreTime.setPosition(Math.randomRange(20, 150), Math.randomRange(10, 110))
})
```

## Step 28 @fullscreen

Next, let's reset the countdown as the player sprite overlaps the taco sprite.

Right click on the ``||sprites: on sprite of Kind Player overlaps otherSprite of kind Food||`` and click **Duplicate**. In the second block, in the kind dropdown, change the ``||sprites: Food||`` kind to ``||sprites: PowerUp||``.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile,
    PowerUp
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
// @highlight
sprites.onOverlap(SpriteKind.Player, SpriteKind.PowerUp, function (sprite, otherSprite) {
    info.changeScoreBy(1)
    otherSprite.destroy()
})
```

## Step 29 @fullscreen

In ``||sprites: on sprite of Kind Player overlaps otherSprite of kind PowerUp||`` block, right click on ``||info: change score by ||`` block and click **Delete Block**.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile,
    PowerUp
}
// @highlight
sprites.onOverlap(SpriteKind.Player, SpriteKind.PowerUp, function (sprite, otherSprite) {
    otherSprite.destroy()
})
```

## Step 30 @fullscreen

Next, let's reset the countdown for when the player overlaps the taco power up.

From the ``||info: Info||`` section, drag the ``||info: start countdown||`` block to the top of the ``||sprites: on sprite of Kind Player overlaps otherSprite of kind PowerUp||`` block.

```blocks
enum SpriteKind {
    Player,
    Enemy,
    Food,
    Projectile,
    PowerUp
}
sprites.onOverlap(SpriteKind.Player, SpriteKind.PowerUp, function (sprite, otherSprite) {
    // @highlight
    info.startCountdown(10)
    otherSprite.destroy()
})
```

## Step 31 @fullscreen

Finally, let's add some obstacles. Obstacles add an extra layer of challenge for the player, adding more chance for error, but also a greater feeling of success.

From the ``||scene: Scene||`` section, drag the ``||scene: set tile map to||`` block in to the ``||loops: on start ||`` block.


```blocks
scene.setBackgroundColor(7)
let mySprite = sprites.create(img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
info.setScore(0)
info.startCountdown(10)
// @highlight
scene.setTileMap(img`
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
    . . . . . . . . . .
`)
```

## Step 32 @fullscreen

Click on grey box inside the ``||scene: set tile map to||`` block choose a color, for example orange, and draw where you'd like obstacles to appear in your game.


```blocks
scene.setBackgroundColor(7)
let mySprite = sprites.create(img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
info.setScore(0)
info.startCountdown(10)
// @highlight
scene.setTileMap(img`
    . . . . . . . . . .
    . . . . . . . . . .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . . . . . . . . . .
    . . . . . . . . . .
`)
```

## Step 33 @fullscreen

From the ``||scene: Scene||`` section, drag the ``||scene: set tile ||`` block in to the end of the ``||loops: on start ||`` block.

In the first grey box, choose the same color you used in your tilemap. Then in the second grey box, go to the **Gallery** and select an obstacle like a rock.


```blocks
scene.setBackgroundColor(7)
let mySprite = sprites.create(img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
info.setScore(0)
info.startCountdown(10)
scene.setTileMap(img`
    . . . . . . . . . .
    . . . . . . . . . .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . . . . . . . . . .
    . . . . . . . . . .
`)
// @highlight
scene.setTile(4, img`
    . . . . . c c b b b . . . . . .
    . . . . c b d d d d b . . . . .
    . . . . c d d d d d d b b . . .
    . . . . c d d d d d d d d b . .
    . . . c b b d d d d d d d b . .
    . . . c b b d d d d d d d b . .
    . c c c c b b b b d d d b b b .
    . c d d b c b b b b b b b b d b
    c b b d d d b b b b b d d b d b
    c c b b d d d d d d d b b b d c
    c b c c c b b b b b b b d d c c
    c c b b c c c c b d d d b c c b
    . c c c c c c c c c c c b b b b
    . . c c c c c b b b b b b b c .
    . . . . . . c c b b b b c c . .
    . . . . . . . . c c c c . . . .
`)
```

# Step 34 @fullscreen

The player can move through the obstacles. They're not doing their job!

Click on the **+** on the ``||scene: set tile ||`` and switch the ``||scene: with wall||`` ``||loops: on||``.

```blocks
scene.setBackgroundColor(7)
let mySprite = sprites.create(img`
    . . . . . f f 4 4 f f . . . . .
    . . . . f 5 4 5 5 4 5 f . . . .
    . . . f e 4 5 5 5 5 4 e f . . .
    . . f b 3 e 4 4 4 4 e 3 b f . .
    . . f 3 3 3 3 3 3 3 3 3 3 f . .
    . f 3 3 e b 3 e e 3 b e 3 3 f .
    . f 3 3 f f e e e e f f 3 3 f .
    . f b b f b f e e f b f b b f .
    . f b b e 1 f 4 4 f 1 e b b f .
    f f b b f 4 4 4 4 4 4 f b b f f
    f b b f f f e e e e f f f b b f
    . f e e f b d d d d b f e e f .
    . . e 4 c d d d d d d c 4 e . .
    . . e f b d b d b d b b f e . .
    . . . f f 1 d 1 d 1 d f f . . .
    . . . . . f f b b f f . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite)
info.setScore(0)
info.startCountdown(10)
scene.setTileMap(img`
    . . . . . . . . . .
    . . . . . . . . . .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . 4 . . . . . . 4 .
    . . . . . . . . . .
    . . . . . . . . . .
`)
// @highlight
scene.setTile(4, img`
    . . . . . c c b b b . . . . . .
    . . . . c b d d d d b . . . . .
    . . . . c d d d d d d b b . . .
    . . . . c d d d d d d d d b . .
    . . . c b b d d d d d d d b . .
    . . . c b b d d d d d d d b . .
    . c c c c b b b b d d d b b b .
    . c d d b c b b b b b b b b d b
    c b b d d d b b b b b d d b d b
    c c b b d d d d d d d b b b d c
    c b c c c b b b b b b b d d c c
    c c b b c c c c b d d d b c c b
    . c c c c c c c c c c c b b b b
    . . c c c c c b b b b b b b c .
    . . . . . . c c b b b b c c . .
    . . . . . . . . c c c c . . . .
`, true)
```

# Congratulations @fullscreen

**Congratulations**, you've created your first full game.

You've learned how to use ``||sprites: Sprites||``, ``||scene: Tiles||``, modify ``||info: Scores||`` and  ``||info: Countdowns||`` and trigger code based on which sprites overlap.

You can share the project with friends or even ``|Download|`` the game for compatible hardware!