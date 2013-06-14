###1.準備
####1.1.githubからDownload
####1.2.マーカーの印刷
###2.Chromeで開く
####2.1Same Origin Policy アクセス制限回避
####2.2使用するカメラの変更
###3.改造する
####3.1.primitiveをだす
####3.2.アニメーションをつける
####3.3.daeをだす
####3.4.mmdをだす
```javascript
enchant();
window.onload = function() {
    var game = new Core();
    game.preload({
        enchant : enchant.png
    });
    game.onload = function() {
        var scene = new ARScene3D();
        var cube = new Cube();
        cube.y = 0.5;
        cube.mesh.texture.src = game.assets['enchant'];
        cube.on('enterframe', function() {
            this.x = 2 * Math.sin(this.age / 10);
            this.rotateYaw(Math.PI / 5);
        })
        scene.base.addChild(cube);
    };
    game.start();
};
```

