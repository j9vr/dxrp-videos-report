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
