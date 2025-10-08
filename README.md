var createScene = function () {
    // This creates a basic Babylon Scene object (non-mesh)
    var scene = new BABYLON.Scene(engine);

    // This creates and positions a free camera (non-mesh)
    var camera = new BABYLON.FreeCamera("camera1", new BABYLON.Vector3(0, 5, -10), scene);

    // This targets the camera to scene origin
    camera.setTarget(BABYLON.Vector3.Zero());

    // This attaches the camera to the canvas
    camera.attachControl(canvas, true);

    // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
    var light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);

    // Default intensity is 1. Let's dim the light a small amount
    light.intensity = 0.7;

    // Our built-in 'ground' shape.
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 6, height: 6}, scene);
    let groundMaterial = new BABYLON.StandardMaterial("Ground Material", scene);
    ground.material = groundMaterial;
    let groundTexture = new BABYLON.Texture(Assets.textures.checkerboard_basecolor_png.path, scene);
    groundMaterial.diffuseColor = BABYLON.Color3.Red();
    ground.material.diffuseTexture = groundTexture;

    BABYLON.ImportMeshAsync(Assets.meshes.Yeti.rootUrl + Assets.meshes.Yeti.filename, scene).then(function({meshes}){
        meshes[0].scaling = new BABYLON.Vector3(0.1, 0.1, 0.1);
    });

    return scene;
};
