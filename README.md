html> 
 
<head> 
 <title>Add Light</title> 
 
 <style> 
  body { 
   margin: 0; 
   overflow: hidden; 
  } 
   
  canvas { 
   background: orange; 
  } 
 </style> 
</head> 
 
<body> 
 
 <canvas id="myCanvas"></canvas> 
 
 <script src="myjs/three.js" ></script>
 <script> 
  //RENDERER 
  var renderer = new THREE.WebGLRenderer( 
  { 
   canvas: document.getElementById('myCanvas'), 
   antialias: true 
  }); 
  renderer.setClearColor(0x0000ff); 
  //0x0000ff => indicate blue color 
 
  renderer.setPixelRatio(window.devicePixelRatio); 
  renderer.setSize(window.innerWidth, window.innerHeight); 
 
  //CAMERA 
  var camera = new THREE.PerspectiveCamera(35, window.innerWidth / window.innerHeight, 0.1, 3000); 
  // var camera = new THREE.OrthographicCamera(window.innerWidth / -2, window.innerWidth / 2, window.innerHeight / 2, window.innerHeight / -2, 0.1, 3000); 
 
  //SCENE 
  var scene = new THREE.Scene(); 
 
  //LIGHTS 
  var light = new THREE.AmbientLight(0xffffff, 0.5); 
  scene.add(light); 
 
  //Point light => shading the front face 
  var light1 = new THREE.PointLight(0xffffff, 0.5); 
  scene.add(light1); 
 
  //OBJECT 
  var geometry = new THREE.CubeGeometry(20, 20, 20); 
  var material = new THREE.MeshLambertMaterial( 
  { 
   color: 0xF3FFE2 
  }); 
 
  var mesh = new THREE.Mesh(geometry, material); 
  mesh.position.set(0, 0, -200); 
  scene.add(mesh); 
 
  //RENDER LOOP 
  requestAnimationFrame(render); 
 
  function render() 
  { 
   mesh.rotation.x += 0.01; 
   mesh.rotation.y += 0.01; 
   renderer.render(scene, camera); 
   requestAnimationFrame(render); 
  } 
 </script> 
</body> 
 
</html>

