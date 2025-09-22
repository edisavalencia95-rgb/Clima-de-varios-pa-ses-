<!DOCTYPE html>

<html lang="es">

<head>

&nbsp; <meta charset="UTF-8">

&nbsp; <title>Clima Interactivo 🌎</title>

&nbsp; <link href="https://fonts.googleapis.com/css2?family=Pacifico\&display=swap" rel="stylesheet">

&nbsp; <style>

&nbsp;   body { 

&nbsp;     font-family: 'Pacifico', cursive;

&nbsp;     text-align: center; 

&nbsp;     padding: 20px; 

&nbsp;     transition: background 1s ease; 

&nbsp;     background: linear-gradient(to right, #74ebd5, #ACB6E5);

&nbsp;     color: white;

&nbsp;   }

&nbsp;   h1 { font-size: 3em; margin-bottom: 20px; }

&nbsp;   .card { 

&nbsp;     border-radius: 15px; 

&nbsp;     padding: 20px; 

&nbsp;     margin: 15px; 

&nbsp;     display: inline-block; 

&nbsp;     width: 250px; 

&nbsp;     box-shadow: 0px 5px 15px rgba(0,0,0,0.2); 

&nbsp;     background: rgba(0,0,0,0.4); 

&nbsp;     transition: transform 0.5s; 

&nbsp;   }

&nbsp;   .card:hover { transform: scale(1.05); }

&nbsp;   .icon { font-size: 50px; margin: 10px; animation: float 3s infinite; }

&nbsp;   @keyframes float {

&nbsp;     0% { transform: translateY(0px); }

&nbsp;     50% { transform: translateY(-10px); }

&nbsp;     100% { transform: translateY(0px); }

&nbsp;   }

&nbsp;   /\* Animaciones extra \*/

&nbsp;   .sun { color: yellow; animation: spin 6s linear infinite; }

&nbsp;   @keyframes spin { 100% { transform: rotate(360deg); } }

&nbsp;   .rain::after {

&nbsp;     content: "💧💧💧";

&nbsp;     display: block;

&nbsp;     font-size: 20px;

&nbsp;     animation: drop 1s infinite;

&nbsp;   }

&nbsp;   @keyframes drop {

&nbsp;     0% { opacity: 0; transform: translateY(-10px); }

&nbsp;     50% { opacity: 1; transform: translateY(10px); }

&nbsp;     100% { opacity: 0; transform: translateY(20px); }

&nbsp;   }

&nbsp; </style>

</head>

<body>

&nbsp; <h1>🌎 Clima Interactivo</h1>

&nbsp; <div id="weather"></div>



&nbsp; <script>

&nbsp;   const apiKey = "TU\_API\_KEY"; // 👈 Pega aquí tu clave de OpenWeatherMap

&nbsp;   const cities = \["Quito", "Madrid", "Londres", "Nueva York", "Tokio", "Buenos Aires"];



&nbsp;   // Colores por país

&nbsp;   const countryColors = {

&nbsp;     "EC": "linear-gradient(to right, yellow, blue, red)",        // Ecuador

&nbsp;     "ES": "linear-gradient(to right, red, yellow, red)",        // España

&nbsp;     "GB": "linear-gradient(to right, navy, white, red)",        // Reino Unido

&nbsp;     "US": "linear-gradient(to right, blue, white, red)",        // Estados Unidos

&nbsp;     "JP": "linear-gradient(to right, white, red)",              // Japón

&nbsp;     "AR": "linear-gradient(to right, skyblue, white, skyblue)"  // Argentina

&nbsp;   };



&nbsp;   // Íconos según clima

&nbsp;   function getWeatherIcon(main) {

&nbsp;     if (main.includes("Clear")) return `<div class="icon sun">☀️</div>`;

&nbsp;     if (main.includes("Cloud")) return `<div class="icon">☁️</div>`;

&nbsp;     if (main.includes("Rain")) return `<div class="icon rain">🌧️</div>`;

&nbsp;     if (main.includes("Snow")) return `<div class="icon">❄️</div>`;

&nbsp;     return `<div class="icon">🌍</div>`;

&nbsp;   }



&nbsp;   async function getWeather(city) {

&nbsp;     const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}\&appid=${apiKey}\&units=metric\&lang=es`;

&nbsp;     const response = await fetch(url);

&nbsp;     return response.json();

&nbsp;   }



&nbsp;   async function showWeather() {

&nbsp;     const container = document.getElementById("weather");

&nbsp;     for (const city of cities) {

&nbsp;       try {

&nbsp;         const data = await getWeather(city);

&nbsp;         const card = document.createElement("div");

&nbsp;         card.className = "card";



&nbsp;         // Fondo según el país

&nbsp;         card.style.background = countryColors\[data.sys.country] || "rgba(0,0,0,0.6)";



&nbsp;         // Contenido

&nbsp;         card.innerHTML = `

&nbsp;           <h2>${data.name} (${data.sys.country})</h2>

&nbsp;           ${getWeatherIcon(data.weather\[0].main)}

&nbsp;           <p>${data.weather\[0].description}</p>

&nbsp;           <p>🌡️ ${data.main.temp} °C</p>

&nbsp;         `;

&nbsp;         container.appendChild(card);

&nbsp;       } catch (error) {

&nbsp;         console.error("Error al obtener clima de", city, error);

&nbsp;       }

&nbsp;     }

&nbsp;   }



&nbsp;   showWeather();

&nbsp; </script>

</body>

</html>

<!DOCTYPE html>

<html lang="es">

<head>

&nbsp; <meta charset="UTF-8">

&nbsp; <title>Clima Interactivo 🌎</title>

&nbsp; <link href="https://fonts.googleapis.com/css2?family=Pacifico\&display=swap" rel="stylesheet">

&nbsp; <style>

&nbsp;   body { 

&nbsp;     font-family: 'Pacifico', cursive;

&nbsp;     text-align: center; 

&nbsp;     padding: 20px; 

&nbsp;     transition: background 1s ease; 

&nbsp;     background: linear-gradient(to right, #74ebd5, #ACB6E5);

&nbsp;     color: white;

&nbsp;   }

&nbsp;   h1 { font-size: 3em; margin-bottom: 20px; }

&nbsp;   .card { 

&nbsp;     border-radius: 15px; 

&nbsp;     padding: 20px; 

&nbsp;     margin: 15px; 

&nbsp;     display: inline-block; 

&nbsp;     width: 250px; 

&nbsp;     box-shadow: 0px 5px 15px rgba(0,0,0,0.2); 

&nbsp;     background: rgba(0,0,0,0.4); 

&nbsp;     transition: transform 0.5s; 

&nbsp;   }

&nbsp;   .card:hover { transform: scale(1.05); }

&nbsp;   .icon { font-size: 50px; margin: 10px; animation: float 3s infinite; }

&nbsp;   @keyframes float {

&nbsp;     0% { transform: translateY(0px); }

&nbsp;     50% { transform: translateY(-10px); }

&nbsp;     100% { transform: translateY(0px); }

&nbsp;   }

&nbsp;   /\* Animaciones extra \*/

&nbsp;   .sun { color: yellow; animation: spin 6s linear infinite; }

&nbsp;   @keyframes spin { 100% { transform: rotate(360deg); } }

&nbsp;   .rain::after {

&nbsp;     content: "💧💧💧";

&nbsp;     display: block;

&nbsp;     font-size: 20px;

&nbsp;     animation: drop 1s infinite;

&nbsp;   }

&nbsp;   @keyframes drop {

&nbsp;     0% { opacity: 0; transform: translateY(-10px); }

&nbsp;     50% { opacity: 1; transform: translateY(10px); }

&nbsp;     100% { opacity: 0; transform: translateY(20px); }

&nbsp;   }

&nbsp; </style>

</head>

<body>

&nbsp; <h1>🌎 Clima Interactivo</h1>

&nbsp; <div id="weather"></div>



&nbsp; <script>

&nbsp;   const apiKey = "TU\_API\_KEY"; // 👈 Pega aquí tu clave de OpenWeatherMap

&nbsp;   const cities = \["Quito", "Madrid", "Londres", "Nueva York", "Tokio", "Buenos Aires"];



&nbsp;   // Colores por país

&nbsp;   const countryColors = {

&nbsp;     "EC": "linear-gradient(to right, yellow, blue, red)",        // Ecuador

&nbsp;     "ES": "linear-gradient(to right, red, yellow, red)",        // España

&nbsp;     "GB": "linear-gradient(to right, navy, white, red)",        // Reino Unido

&nbsp;     "US": "linear-gradient(to right, blue, white, red)",        // Estados Unidos

&nbsp;     "JP": "linear-gradient(to right, white, red)",              // Japón

&nbsp;     "AR": "linear-gradient(to right, skyblue, white, skyblue)"  // Argentina

&nbsp;   };



&nbsp;   // Íconos según clima

&nbsp;   function getWeatherIcon(main) {

&nbsp;     if (main.includes("Clear")) return `<div class="icon sun">☀️</div>`;

&nbsp;     if (main.includes("Cloud")) return `<div class="icon">☁️</div>`;

&nbsp;     if (main.includes("Rain")) return `<div class="icon rain">🌧️</div>`;

&nbsp;     if (main.includes("Snow")) return `<div class="icon">❄️</div>`;

&nbsp;     return `<div class="icon">🌍</div>`;

&nbsp;   }



&nbsp;   async function getWeather(city) {

&nbsp;     const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}\&appid=${apiKey}\&units=metric\&lang=es`;

&nbsp;     const response = await fetch(url);

&nbsp;     return response.json();

&nbsp;   }



&nbsp;   async function showWeather() {

&nbsp;     const container = document.getElementById("weather");

&nbsp;     for (const city of cities) {

&nbsp;       try {

&nbsp;         const data = await getWeather(city);

&nbsp;         const card = document.createElement("div");

&nbsp;         card.className = "card";



&nbsp;         // Fondo según el país

&nbsp;         card.style.background = countryColors\[data.sys.country] || "rgba(0,0,0,0.6)";



&nbsp;         // Contenido

&nbsp;         card.innerHTML = `

&nbsp;           <h2>${data.name} (${data.sys.country})</h2>

&nbsp;           ${getWeatherIcon(data.weather\[0].main)}

&nbsp;           <p>${data.weather\[0].description}</p>

&nbsp;           <p>🌡️ ${data.main.temp} °C</p>

&nbsp;         `;

&nbsp;         container.appendChild(card);

&nbsp;       } catch (error) {

&nbsp;         console.error("Error al obtener clima de", city, error);

&nbsp;       }

&nbsp;     }

&nbsp;   }



&nbsp;   showWeather();

&nbsp; </script>

</body>

</html>



