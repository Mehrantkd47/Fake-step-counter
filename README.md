# Fake-step-counter
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fake Step Counter</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f8ff;
      text-align: center;
      padding: 20px;
    }
    h1 {
      color: #2a9d8f;
    }
    button {
      padding: 10px 20px;
      margin-top: 10px;
      background: #2a9d8f;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background: #21867a;
    }
    .info {
      margin-top: 10px;
      font-size: 14px;
      color: #555;
    }
  </style>
</head>
<body>
  <div class="app-container">
    <h1>Fake Step Counter</h1>
    <p>Total Steps: <span id="step-counter">0</span></p>
    <button id="fake-step-btn">Add Fake Steps</button>
    <p class="info">Move your phone or tap the button to count fake steps!</p>
  </div>

  <script>
    let stepCounter = 0;

    // Access accelerometer data
    if (window.DeviceMotionEvent) {
      window.addEventListener('devicemotion', (event) => {
        const acceleration = event.accelerationIncludingGravity;

        // Detect fake motion and add random steps
        if (acceleration.x > 1 || acceleration.y > 1 || acceleration.z > 1) {
          stepCounter += Math.floor(Math.random() * 3) + 1;
          updateStepCounter();
        }
      });
    } else {
      alert('Device motion not supported on this device.');
    }

    // Add fake steps on button click
    document.getElementById('fake-step-btn').addEventListener('click', () => {
      stepCounter += Math.floor(Math.random() * 10) + 5;
      updateStepCounter();
    });

    // Update the step counter display
    function updateStepCounter() {
      document.getElementById('step-counter').textContent = stepCounter;
    }
  </script>
</body>
</html>
