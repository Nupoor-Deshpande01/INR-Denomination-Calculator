# INR-Denomination-Calculator
This is my first website using HTML, CSS and JavaScript. 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title> INR Denomination Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }
        .container {
            width: 50%;
            margin: 50px auto;
            background: rgb(255, 255, 255);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, button {
            padding: 10px;
            margin: 10px;
            font-size: 16px;
        }
        #result {
            margin-top: 20px;
            text-align: left;
        }
    </style>
</head>
<body background = "https://m.economictimes.com/thumb/msid-112305172,width-1200,height-900,resizemode-4,imgsize-46758/indian-rupee-weakens-to-hit-record-low-hurt-by-weak-asia-fx.jpg" >
    <div class="container">
        <h2 style="color:crimson">INR Denomination Calculator</h2>
        <input type="number" id="amount" placeholder="Enter the amount">
        <button style="color:green" onclick="calculateDenomination()">Calculate</button>
        <div id="result"></div>
    </div>

    <script>
        function calculateDenomination() {
            let amount = parseInt(document.getElementById('amount').value);
            let resultDiv = document.getElementById('result');
            resultDiv.innerHTML = '';

            if (isNaN(amount) || amount <= 0) {
                resultDiv.innerHTML = '<p style="color:red;">Enter a valid positive amount.</p>';
                return;
            }

            let notes = [2000, 500, 200, 100, 50, 20, 10];
            let coins = [10, 5, 2, 1];
            
            resultDiv.innerHTML = '<h3 style="color:blue;">Denomination of the amount:</h3>';
            
            notes.forEach(note => {
                let count = Math.floor(amount / note);
                amount %= note;
                if (count > 0) {
                    resultDiv.innerHTML += `<p>Rs. ${note} note count: ${count}</p>`;
                }
            });

            coins.forEach(coin => {
                let count = Math.floor(amount / coin);
                amount %= coin;
                if (count > 0) {
                    resultDiv.innerHTML += `<p>Rs. ${coin} coin count: ${count}</p>`;
                }
            });
        }
    </script>
</body>
</html>

