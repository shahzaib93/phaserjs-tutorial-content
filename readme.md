# Guidlines for this Tutorial 🤓

- Step 0: Create `index.html`, link phaserJs and create `game.js` file
- Step 1: Create an empty game:
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
  - Explain `new` operator, `Game({...})` as well as input parameters
  
- Step 2: Create `assets` folder and explain items
- Step 3: Explain `scene` concept in PhaserJS
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

```javascript
 preload() {
    this.load.image('player', 'assets/player.png');
    this.load.image('coin', 'assets/coin.png');
 }
 ```
 
 - Step 5: Create assets and fill up `create` function without keyboard
 ```javascript
 create() {
    this.player = this.physics.add.sprite(100, 100, 'player');
    this.coin = this.physics.add.sprite(300, 200, 'coin');

    this.score = 0;
    let style = { font: '20px Arial', fill: '#fff' };
    this.scoreText = this.add.text(20, 20, 'score: ' + this.score, style);
  }
```

- Step 6: Add keyboard handler
```javascript
create() {
    this.player = this.physics.add.sprite(100, 100, 'player');
    this.coin = this.physics.add.sprite(300, 200, 'coin');

    this.score = 0;
    let style = { font: '20px Arial', fill: '#fff' };
    this.scoreText = this.add.text(20, 20, 'score: ' + this.score, style);

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

- Step 7: Add collision concept, by adding following code to beginning of `update()` function and implement `hit()` function (Skip `tween` function).
```javascript
if (this.physics.overlap(this.player, this.coin)) {
      this.hit();
}
```

```javascript
hit() {
    this.coin.x = Phaser.Math.Between(100, 600);
    this.coin.y = Phaser.Math.Between(100, 200);

    this.score += 10;
    this.scoreText.setText('score: ' + this.score);
}
```

- For each step, run the app and shows the result plus explanation.
- For each step create a folder `step n` and keep a copy of all files for `step n`.
- Within each folder, create a subfolder called `lecture` and keep:
  - A markdown file contains tutorial content.
  - A text script file for voice over for that step
  - Any extra images or resources you need to mention within the tuorial
  - Create a file like `practice.js` contains up to 5 challenges for students relevant to step topic.


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
