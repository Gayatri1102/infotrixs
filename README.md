This example uses Bootstrap classes for the container and form control to enhance the layout and appearance. The design remains responsive, adapting to different screen sizes. Users can input a city name in the provided text field, and the weather information updates accordingly.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <style>
        body {
            font-family: 'Helvetica', sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
        }

        #menu {
            position: absolute;
            top: 10px;
            right: 10px;
            cursor: pointer;
            color: #007bff;
            font-size: 18px;
        }

        #menu:hover {
            text-decoration: underline;
        }

        #weather-container {
            background-color: #fff;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
            max-width: 400px;
            width: 90%;
        }

        #city {
            font-size: 24px;
            margin-bottom: 10px;
        }

        #temperature {
            font-size: 48px;
            margin: 20px 0;
        }

        #time {
            font-size: 16px;
            color: #666;
        }

        #cityInput {
            display: none;
            margin-top: 10px;
            padding: 5px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div id="menu" onclick="showCityInput()">Change City</div>

    <div id="weather-container" class="container">
        <div id="city">City Name</div>
        <div id="temperature">23°C</div>
        <div id="time">Last updated: 12:30 PM</div>
        <input type="text" id="cityInput" class="form-control" placeholder="Enter City" onblur="updateWeather()">
    </div>

    <!-- Bootstrap JS and Popper.js (required for Bootstrap) -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.10.2/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

    <script>
        function showCityInput() {
            document.getElementById('cityInput').style.display = 'block';
            document.getElementById('cityInput').focus();
        }

        function updateWeather() {
            const cityName = document.getElementById('cityInput').value || 'Pune';

            // In a real-world scenario, you would fetch data from an API
            // For simplicity, using static data here
            const weatherData = {
                city: cityName,
                temperature: '28°C',
                time: new Date().toLocaleTimeString(),
            };

            // Update the HTML with the fetched data
            document.getElementById('city').innerText = weatherData.city;
            document.getElementById('temperature').innerText = weatherData.temperature;
            document.getElementById('time').innerText = 'Last updated: ' + weatherData.time;

            // Hide the city input field after updating weather
            document.getElementById('cityInput').style.display = 'none';
        }

        // Initial update on page load
        updateWeather();

        // Update weather every 5 minutes (300,000 milliseconds)
        setInterval(updateWeather, 300000);
    </script>
</body>
</html>

