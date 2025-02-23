<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 20px;
            background-color: #3498db; /* Changed background color */
        }
        
        #age-form {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        label {
            margin-bottom: 10px;
        }
        
        input[type="date"] {
            padding: 10px;
            margin-bottom: 20px;
        }
        
        #calculate-btn {
            padding: 10px 15px;
            background-color: #030910;
            color: white;
            border: none;
            cursor: pointer;
        }
        
        #calculate-btn:hover {
            background-color: #0056b3;
        }
        
        #result {
            margin-top: 20px;
            font-size: 1.2em;
        }
        
        #current-date {
            margin-top: 20px;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <h1>Age Calculator</h1>
    <form id="age-form">
        <label for="dob">Enter your Date of Birth:</label>
        <input type="date" id="dob" required>
        <button id="calculate-btn">Calculate Age</button>
    </form>
    <div id="result"></div>
    <div id="current-date"></div>

    <script>
        const form = document.getElementById('age-form');
        const resultDiv = document.getElementById('result');
        const currentDateDiv = document.getElementById('current-date');

        // Display current date
        function displayCurrentDate() {
            const today = new Date();
            const year = today.getFullYear();
            const month = (today.getMonth() + 1).toString().padStart(2, '0');
            const day = today.getDate().toString().padStart(2, '0');
            currentDateDiv.innerText = `Current Date: ${day}/${month}/${year}`;
        }

        displayCurrentDate();

        form.addEventListener('submit', (e) => {
            e.preventDefault();
            const dobInput = document.getElementById('dob');
            const dob = new Date(dobInput.value);
            const today = new Date();
            let years = today.getFullYear() - dob.getFullYear();
            let months = today.getMonth() - dob.getMonth();
            let days = today.getDate() - dob.getDate();

            if (months < 0) {
                years--;
                months += 12;
            }

            if (days < 0) {
                months--;
                days += new Date(today.getFullYear(), today.getMonth(), 0).getDate();
            }

            resultDiv.innerText = `Your age is: ${years} years, ${months} months, and ${days} days`;
        });
    </script>
</body>
</html> 
