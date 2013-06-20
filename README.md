#ar.gl.enchant.js
このライブラリはMITライセンスのもとで利用可能です。
このライブラリに付属するライブラリはコード内のライセンス記載に従い再配布しています。
###1. 準備
####1.1. githubからDownload
[Download Zip file](https://github.com/shellkana/ar.gl.enchant.js/archive/master.zip)
####1.2. マーカーの印刷
<img src="1001.png" width="70" height="70" >
###2. Chromeで開く
####2.1. Same Origin Policy アクセス制限回避
gl.enchant.jsではローカルのファイルを読み込む際にセキュリティーポリシーに引っかかります。  
詳しくは[Starting with enchant.js](http://enchantjs.com/ja/resource-ja/starting-with-enchant-js/)の解説を参照ください。  
起動オプションの指定は[Chromeのローカルセキュリティポリシーの回避](http://dev.classmethod.jp/etc/chrome-localfile-security/)を参考にするとよいです。
####2.2. 使用するカメラの変更
以下は、USBのWebカメラを利用する場合の手順です。  
1.設定【chrome://settings/】をひらく  
2.下方の詳細設定を表示をクリック  
3.プライバシーのコンテンツの設定をクリック  
4.下から２番目のメディアのカメラの部分を変更
####2.3. 開き方の注意
samples/sample1フォルダのindex.htmlをChromeにドラッグ&ドロップで開きます。  
Macではダブルクリックで開くとカメラが起動しなくなります。
###3. 改造する
####3.1. primitiveをだす
samples/sample1フォルダのmain.jsをテキストエディタで開きます。
```javascript
enchant();
window.onload = function() {
    var game = new Core(960, 640);
    game.onload = function() {
        var scene = new ARScene3D();
        var cube = new Cube();
        cube.z = 0.5;
        scene.base.addChild(cube);
    };
    game.start();
};
```
6行目のCubeをSphere、Torus、Cylinderなどに変えてみましょう。  
7行目を参考にx,y,zのプロパティを変化させて遊んでみましょう。  
```javascript
enchant();
window.onload = function() {
    var game = new Core(960, 640);
    game.onload = function() {
        var scene = new ARScene3D();
        var cube = new Cube();
        cube.z = 0.5;
        scene.base.addChild(cube);
        var sphere = new Sphere();
        sphere.z = 0.5;
        sphere.x = 1;
        scene.base.addChild(sphere);
    };
    game.start();
};
```
このように書くことで球と直方体を共存できます。  
baseはマーカーに重なるように配置されたPlaneXYを指します。
####3.2. アニメーションをつける
####3.3. daeをだす
####3.4. mmdをだす
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

