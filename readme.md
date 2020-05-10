# Guidelines for this Tutorial 🤓

Hi, 🤚 This repository has been created for content developers interested in being part of our team to develop online programming courses for kids and teens within our online platform. You are supposed to follow guidelines here and create a short course. When you are done, you should share your repository with us, and we will check and back to you.

 This course is about teaching Javascript with PhaserJS. The output of this little game is available [here](https://unclecode.github.io/phaserjs-tutorial-content/).

👉 I have recorded a video to explain this guideline, you can watch it [here](https://www.loom.com/share/00c1f996fc5145b2a36bd48eb909b49b).

## Steps:
- Step 0: Create `index.html`, add a script tag to the PhaserJs CDN, and create the `game.js` file.
  - Go through of `index.html` and explain elements special `div#game` element 
 
- Step 1: Create the game object. In this step we are focusing on the concept of object:
```javascript
new Phaser.Game({
  width: 700,
  height: 300,
  backgroundColor: '#3498db',
  scene: mainScene,
  physics: { default: 'arcade' },
  parent: 'game',
});
```
  - Explain about following parts:
    - `new` operator
    - `Game({...})` constructot
    - Input parameters
  
- Step 2: Create `assets` folder and explain items within it.
- Step 3: Explain `scene` concept in PhaserJS, You can follow the given code below to illustrate the scene life cysle for students. Focus is on the concept of `class` and `function`.
```javascript
class mainScene {
  // explain scene life cycle
  preload() {
    // Explain when and how this function is invoking
  }
  create() {
    // Explain when and how this function is invoking  
  }
  update() {
    // Explain when and how this function is invoking
  }
}
```

- Step 4: Load assets:
  - Explain why `preload()` is the best place for loading
  - Explain `this` keyword

```javascript
 preload() {
    this.load.image('player', 'assets/player.png');
    this.load.image('coin', 'assets/coin.png');
 }
 ```
 
 - Step 5: Create assets and implement `create()` function without scoring and handeling keyboard event. In this step we explain more on event-driving model as well if `if` conditional structure.
 ```javascript
 create() {
    this.player = this.physics.add.sprite(100, 100, 'player');
    this.coin = this.physics.add.sprite(300, 200, 'coin');
  }
```

- Step 6: Add keyboard handler. 
  - Explain `CursorKeys()`
  - Explain `update()` function
  - Explain cartesian coordinate system 
```javascript
create() {
    // previous code
    this.arrow = this.input.keyboard.createCursorKeys();
  }

  update() {
    if (this.arrow.right.isDown) {
      this.player.x += 3;
    } else if (this.arrow.left.isDown) {
      this.player.x -= 3;
    } 

    if (this.arrow.down.isDown) {
      this.player.y += 3;
    } else if (this.arrow.up.isDown) {
      this.player.y -= 3;
    } 
  }
```

- Step 7: Implement the collision between coin and player. In this part, we are focusing on the control structure(`if`) to check if two objects have collision or not. Use the boolean version of the `overlap` function between the coin and player by adding the following code at the beginning of the `update()` function.
```javascript
if (this.physics.overlap(this.player, this.coin)) {
      console.log('💥')
}
```
  - Run the code and show it works

- Step 8: Add `hit()` function. In this step we focus on concept of `function()`. First you add the code in the if body within the `update()` function, then explain the benefit of modularity and move it into new function `hit()`.
```javascript
hit() {
    this.coin.x = Phaser.Math.Between(100, 600);
    this.coin.y = Phaser.Math.Between(100, 200);
}
```

    
- Step 9: Add scoring. First explain the scoring concept that we get 10+ on each hit. Then invite students to think on what changes should be done, like 1) Add a text label to show score which should be done in `create()`, 2) update the text label on hit which should be done within `hit()` function which is part of `update()` cycle. In this way students get more familiar with differences between preload/creat/update.
```javascript
create() {
  // previoud code
   this.score = 0;
   let style = { font: '20px Arial', fill: '#fff' };
   this.scoreText = this.add.text(20, 20, 'score: ' + this.score, style);
 }
 
 hit() {
  // previoud code
   this.score += 10;
   this.scoreText.setText('score: ' + this.score);
 }
```

## Consider the following points:
- For each step, run the app and shows the result plus explanation.
- For each step, create a folder `stepN` and keep a copy of all files for `stepN`.
- Within each folder, create a subfolder called `lecture` and keep:
  - A markdown file contains tutorial content.
  - A text script file for voice over for that step
  - Any extra images or resources you need to mention within the tutorial
  - Create a file like `practice.js` contains up to 5 challenges for students relevant to the step topic.


## Folder Structure 

```yaml
- root folder
  - step 0
    - index.html
    - game.js
    - lecture 
      - lecture.md
      - script.txt
  - step 1
    - index.html
    - game.js
    - lecture 
      - lecture.md
      - script.txt
  ...
```

