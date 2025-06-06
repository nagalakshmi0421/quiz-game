<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Modern Calculator</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    .glass {
      background: rgba(255, 255, 255, 0.1);
      border-radius: 20px;
      box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
      backdrop-filter: blur(8.5px);
      -webkit-backdrop-filter: blur(8.5px);
      border: 1px solid rgba(255, 255, 255, 0.18);
    }
  </style>
</head>
<body class="bg-gradient-to-br from-gray-800 to-gray-900 min-h-screen flex items-center justify-center text-white transition-colors">

  <div class="w-full max-w-sm p-5 glass">
    <div class="flex justify-between items-center mb-4">
      <h1 class="text-2xl font-bold">🧮 Calculator</h1>
      <button id="themeToggle" class="text-sm bg-white text-black px-2 py-1 rounded hover:bg-gray-200 transition">Toggle Theme</button>
    </div>
    <input id="display" class="w-full text-right text-2xl bg-white text-black rounded px-4 py-2 mb-4" type="text" readonly />

    <div class="grid grid-cols-4 gap-2">
      <button class="btn">7</button>
      <button class="btn">8</button>
      <button class="btn">9</button>
      <button class="btn text-red-500">DEL</button>

      <button class="btn">4</button>
      <button class="btn">5</button>
      <button class="btn">6</button>
      <button class="btn">+</button>

      <button class="btn">1</button>
      <button class="btn">2</button>
      <button class="btn">3</button>
      <button class="btn">-</button>

      <button class="btn">0</button>
      <button class="btn">.</button>
      <button class="btn">=</button>
      <button class="btn">/</button>

      <button class="btn col-span-2">C</button>
      <button class="btn">*</button>
      <button class="btn">%</button>
    </div>
  </div>

  <script>
    const display = document.getElementById("display");
    const buttons = document.querySelectorAll(".btn");
    const themeToggle = document.getElementById("themeToggle");
    let dark = true;

    buttons.forEach((btn) => {
      btn.addEventListener("click", () => {
        const value = btn.textContent;
        if (value === "=") {
          try {
            display.value = eval(display.value);
          } catch {
            display.value = "Error";
          }
        } else if (value === "C") {
          display.value = "";
        } else if (value === "DEL") {
          display.value = display.value.slice(0, -1);
        } else {
          display.value += value;
        }
      });
    });

    themeToggle.addEventListener("click", () => {
      dark = !dark;
      document.body.classList.toggle("bg-gray-900", dark);
      document.body.classList.toggle("bg-white", !dark);
      document.body.classList.toggle("text-white", dark);
      document.body.classList.toggle("text-black", !dark);
    });
  </script>

  <style>
    .btn {
      padding: 0.75rem;
      font-size: 1.25rem;
      background-color: rgba(255, 255, 255, 0.15);
      border-radius: 10px;
      transition: 0.2s;
    }

    .btn:hover {
      background-color: rgba(255, 255, 255, 0.3);
      transform: scale(1.05);
    }
  </style>
</body>
</html>

