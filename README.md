<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Streamable Clone</title>
  <link rel="stylesheet" href="style.css">
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.23.0/firebase-storage-compat.js"></script>
</head>
<body>
  <div class="container">
    <h1>Streamable Clone</h1>
    <input type="file" id="videoInput" accept="video/*">
    <button id="uploadBtn">Upload & Play</button>

    <div class="video-container">
      <video id="videoPlayer" controls></video>
    </div>

    <div id="videoList">
      <h2>Uploaded Videos</h2>
      <ul id="videos"></ul>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
