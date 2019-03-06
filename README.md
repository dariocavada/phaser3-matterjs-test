# phaser3-matterjs-test
Phaser3 matterjs physics using TexturePacker and Physics Editor tools

We use TexturePacket to create spritesheet and PhysicsEditor to create shapes

## Use Phaser3 and MatterJS Physics

### Test 01: Physics with texture packer + physics editor 
In the following code I've have added `this.matter.add.mouseSpring();`
but there are some problems. 

If you try to drag orange it works, and even if you drag cherries inside the circles.


(I've enabled the matterjs debug so the physics lines are drawn around objects ).

If you try to drag the crate or the banana, dragging does not work.

<script src="https://gist.github.com/dariocavada/3e6497718729d475f3cfe2e929769fcc.js"></script>

### Test 02: Physics with texture packer (without using a shape mouse dragging using matterjs works)

### Test 03: Physics with texture packer + physics editor (work around using PhaserJS 3 dragging)

