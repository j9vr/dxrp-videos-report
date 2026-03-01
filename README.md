<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Local Video Streamer</title>
<style>
body { font-family: Arial; background:#111; color:#eee; text-align:center; }
input, button { padding:10px; margin:5px; }
video { width:80%; max-height:400px; margin-top:20px; }
ul { list-style:none; padding:0; }
li { margin:5px 0; }
</style>
</head>
<body>

<h1>Local Video Streamer</h1>

<input type="file" id="videoInput" accept="video/*">
<button id="uploadBtn">Play Video</button>

<video id="videoPlayer" controls></video>

<h2>Uploaded Videos</h2>
<ul id="videos"></ul>

<script>
const videoInput = document.getElementById('videoInput');
const uploadBtn = document.getElementById('uploadBtn');
const videoPlayer = document.getElementById('videoPlayer');
const videosList = document.getElementById('videos');

let videos = [];

function renderVideos() {
  videosList.innerHTML = '';
  videos.forEach((v,i)=>{
    const li = document.createElement('li');
    li.textContent = v.name;
    const btn = document.createElement('button');
    btn.textContent='Play';
    btn.onclick=()=>{ videoPlayer.src=v.url; videoPlayer.play(); }
    li.appendChild(btn);
    videosList.appendChild(li);
  });
}

uploadBtn.onclick = ()=>{
  const file = videoInput.files[0];
  if(!file) return alert('Select a video');
  const url = URL.createObjectURL(file);
  videos.push({name:file.name,url});
  renderVideos();
  videoPlayer.src=url;
  videoPlayer.play();
}
</script>

</body>
</html>
