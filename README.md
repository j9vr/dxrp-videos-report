body {
  font-family: Arial, sans-serif;
  background-color: #111;
  color: #eee;
  display: flex;
  justify-content: center;
  padding: 20px;
}

.container {
  max-width: 700px;
  width: 100%;
}

h1 {
  text-align: center;
  margin-bottom: 20px;
}

input, button {
  padding: 10px;
  margin: 5px 0;
  width: 100%;
  box-sizing: border-box;
}

button {
  background-color: #28a745;
  border: none;
  color: white;
  cursor: pointer;
  font-size: 16px;
}

button:hover {
  background-color: #218838;
}

.video-container {
  margin-top: 20px;
  text-align: center;
}

video {
  width: 100%;
  max-height: 400px;
  background-color: black;
}

#videoList ul {
  list-style: none;
  padding-left: 0;
}

#videoList li {
  margin: 5px 0;
}

#videoList li button {
  width: auto;
  margin-left: 10px;
  background-color: #007bff;
}

#videoList li button:hover {
  background-color: #0056b3;
}
