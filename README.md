# phaser3-matterjs-test
Phaser3 matterjs physics using TexturePacker and Physics Editor tools

We use TexturePacket to create spritesheet and PhysicsEditor to create shapes

## Use Phaser3 and MatterJS Physics

**Online demos:**

http://dariocavada.com/static/public/phaser3matterjsTest/

### Test 01: 
**Physics with texture packer + physics editor**

In the following code I've have added `this.matter.add.mouseSpring();`
but there are some problems. 

If you try to drag the orange it works, and even if you drag the cherries inside the circles.

(I've enabled the matterjs debug so the physics lines are drawn around objects ).

If you try to drag the crate or the banana, dragging does not work.

```javascript
this.matter.add.sprite(200, 50, 'sheet', 'crate', {shape: shapes.crate});
this.matter.add.sprite(250, 250, 'sheet', 'banana', {shape: shapes.banana});
this.matter.add.sprite(360, 50, 'sheet', 'orange', {shape: shapes.orange});
this.matter.add.sprite(400, 250, 'sheet', 'cherries', {shape: shapes.cherries});

this.matter.add.mouseSpring();
```

### Test 02
**Physics with texture packer.**

Without using the shape option, mouse dragging using matterjs works.

```javascript
this.matter.add.sprite(200, 50, 'sheet', 'crate');
this.matter.add.sprite(250, 250, 'sheet', 'banana');
this.matter.add.sprite(360, 50, 'sheet', 'orange');
this.matter.add.sprite(400, 250, 'sheet', 'cherries');

this.matter.add.mouseSpring();
```

### Test 03
**Physics with texture packer + physics editor**

The following code is a work around using PhaserJS 3 dragging system.
So you have to put `setInteractive()` and `setDraggable()` on one object and then use `this.input.on('drag', ... )` function to move the object according to the pointer coordinates. 

But in this case the physical system does not seem to respond smoothly as in the first and second example...

```javascript
   var mattersprites = { };
    mattersprites.crate = this.matter.add.sprite(200, 50, 'sheet', 'crate', {shape: shapes.crate});
    mattersprites.banana = this.matter.add.sprite(250, 250, 'sheet', 'banana', {shape: shapes.banana});
    mattersprites.orange = this.matter.add.sprite(360, 50, 'sheet', 'orange', {shape: shapes.orange});
    mattersprites.cherries = this.matter.add.sprite(400, 250, 'sheet', 'cherries', {shape: shapes.cherries});

    mattersprites.crate.setInteractive();
    this.input.setDraggable(mattersprites.crate);

    mattersprites.banana.setInteractive();
    this.input.setDraggable(mattersprites.banana);

    mattersprites.orange.setInteractive();
    this.input.setDraggable(mattersprites.orange);

    mattersprites.cherries.setInteractive();
    this.input.setDraggable(mattersprites.cherries);

    this.input.on('drag', function (pointer, gameObject, dragX, dragY) {
            gameObject.x = dragX;
            gameObject.y = dragY;
    });
```
