# CS<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Details</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f9;
      margin: 0;
      padding: 20px;
    }
    .container {
      max-width: 500px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }
    h1 { text-align: center; }
    label { display: block; margin-top: 10px; }
    input, textarea {
      width: 100%;
      padding: 8px;
      margin-top: 4px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      margin-top: 15px;
      padding: 10px;
      width: 100%;
      border: none;
      border-radius: 4px;
      background: #007bff;
      color: #fff;
      font-size: 16px;
      cursor: pointer;
    }
    button:hover { background: #0056b3; }
    .output {
      margin-top: 20px;
      padding: 10px;
      background: #e9ecef;
      border-radius: 4px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Store My Details</h1>
    <form id="detailsForm">
      <label for="name">Full Name:</label>
      <input type="text" id="name" required>

      <label for="email">Email:</label>
      <input type="email" id="email" required>

      <label for="phone">Phone:</label>
      <input type="tel" id="phone">

      <label for="about">About Me:</label>
      <textarea id="about"></textarea>

      <button type="submit">Save Details</button>
    </form>

    <div class="output" id="output">
      <h3>Saved Details:</h3>
      <pre id="savedData">No details saved yet.</pre>
    </div>
  </div>

  <script>
    const form = document.getElementById('detailsForm');
    const savedData = document.getElementById('savedData');

    // Load saved data on page load
    window.onload = () => {
      const data = localStorage.getItem('myDetails');
      if (data) savedData.textContent = data;
    };

    form.addEventListener('submit', e => {
      e.preventDefault();
      const details = {
        name: document.getElementById('name').value,
        email: document.getElementById('email').value,
        phone: document.getElementById('phone').value,
        about: document.getElementById('about').value
      };
      const dataString = JSON.stringify(details, null, 2);
      localStorage.setItem('myDetails', dataString);
      savedData.textContent = dataString;
      alert('Details saved locally in your browser!');
    });
  </script>
</body>
</html>
