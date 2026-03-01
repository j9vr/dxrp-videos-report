<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mini Streamable</title>
<style>
body { font-family: Arial; background:#111; color:#eee; text-align:center; }
input, button { padding:10px; margin:5px; }
video { width:80%; max-height:400px; margin-top:20px; }
ul { list-style:none; padding:0; }
li { margin:5px 0; }
a { color: #0d6efd; text-decoration: underline; }
</style>

<!-- Firebase SDKs -->
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-storage-compat.js"></script>
</head>
<body>

<h1>Mini Streamable</h1>

<input type="file" id="videoInput" accept="video/*">
<button id="uploadBtn">Upload Video</button>

<video id="videoPlayer" controls></video>

<h2>Uploaded Videos</h2>
<ul id="videos"></ul>

<script src="script.js"></script>
</body>
</html>
// ==== Replace this with YOUR Firebase config ====
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};

firebase.initializeApp(firebaseConfig);
const storage = firebase.storage();

const videoInput = document.getElementById('videoInput');
const uploadBtn = document.getElementById('uploadBtn');
const videoPlayer = document.getElementById('videoPlayer');
const videosList = document.getElementById('videos');

let videos = [];

function renderVideos() {
  videosList.innerHTML = '';
  videos.forEach(v => {
    const li = document.createElement('li');
    li.textContent = v.name + ' → ';

    const playBtn = document.createElement('button');
    playBtn.textContent = 'Play';
    playBtn.onclick = () => { videoPlayer.src = v.url; videoPlayer.play(); }

    const link = document.createElement('a');
    link.href = v.url;
    link.target = '_blank';
    link.textContent = 'Share URL';

    li.appendChild(playBtn);
    li.appendChild(document.createTextNode(' '));
    li.appendChild(link);
    videosList.appendChild(li);
  });
}

uploadBtn.onclick = () => {
  const file = videoInput.files[0];
  if (!file) return alert('Select a video');

  const storageRef = storage.ref('videos/' + Date.now() + '_' + file.name);
  const uploadTask = storageRef.put(file);

  uploadTask.on('state_changed',
    snapshot => {}, 
    error => console.error(error),
    () => {
      uploadTask.snapshot.ref.getDownloadURL().then(url => {
        videos.push({ name: file.name, url });
        renderVideos();
        videoPlayer.src = url;
        videoPlayer.play();
        videoInput.value = '';
      });
    }
  );
};
