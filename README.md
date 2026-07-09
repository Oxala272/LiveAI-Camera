# LiveAI-Camera
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LiveAI Camera</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

<h1>LiveAI Camera</h1>

<video id="video" autoplay playsinline muted></video>

<div class="controls">
  <button id="startCamera">Start Camera</button>
</div>

<script src="app.js"></script>

</body>
</html>
body{
    margin:0;
    background:#111;
    color:white;
    font-family:Arial,sans-serif;
    text-align:center;
}

h1{
    margin-top:20px;
}

video{
    width:95%;
    max-width:500px;
    border-radius:20px;
    margin-top:20px;
}

button{
    margin-top:20px;
    padding:15px 30px;
    border:none;
    border-radius:15px;
    font-size:18px;
    cursor:pointer;
}
const video = document.getElementById("video");
const startButton = document.getElementById("startCamera");

startButton.addEventListener("click", async () => {
    try {
        const stream = await navigator.mediaDevices.getUserMedia({
            video: {
                facingMode: "user"
            },
            audio: false
        });

        video.srcObject = stream;

    } catch(err){
        alert("Camera permission denied.");
        console.error(err);
    }
});