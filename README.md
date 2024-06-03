<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GOTH EEG FAN REGISTRATION</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #2c2c2c;
            color: #e0e0e0;
            margin: 0;
            padding: 0;
            text-align: center;
        }
        header {
            background-color: #1a1a1a;
            padding: 20px;
            font-size: 1.5em;
            color: #e0e0e0;
        }
        .container {
            margin: 20px;
            padding: 20px;
            border-radius: 10px;
            background-color: #3a3a3a;
        }
        input, select {
            margin: 10px 0;
            padding: 10px;
            border-radius: 5px;
            border: none;
            width: 100%;
        }
        button {
            background-color: #5a5a5a;
            color: #e0e0e0;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #767676;
        }
        .hidden {
            display: none;
        }
    </style>
</head>
<body>
    <header>GOTH EEG FAN REGISTRATION</header>
    
    <div id="page1" class="container">
        <h2>Sign Up</h2>
        <form id="signupForm">
            <input type="text" id="name" name="name" placeholder="Name" required>
            <input type="email" id="email" name="email" placeholder="Email" required>
            <input type="file" id="profilePicture" name="profilePicture" accept="image/*" required>
            <button type="button" onclick="showPage(2)">Next</button>
        </form>
    </div>
    
    <div id="page2" class="container hidden">
        <h2>Your Profile</h2>
        <p>Name: <span id="displayName"></span></p>
        <p>Email: <span id="displayEmail"></span></p>
        <p>Profile Picture:</p>
        <img id="displayProfilePicture" src="" alt="Profile Picture" style="width:150px;">
        <button type="button" onclick="showPage(3)">Next</button>
    </div>
    
    <div id="page3" class="container hidden">
        <h2>Subscription</h2>
        <p>Subscription cost: $100</p>
        <p>Do you agree?</p>
        <button type="button" onclick="showPage(4)">Yes</button>
    </div>
    
    <div id="page4" class="container hidden">
        <h2>Mode of Payment</h2>
        <select id="paymentMethod" name="paymentMethod" required>
            <option value="">Select a payment method</option>
            <option value="cashapp">CashApp</option>
            <option value="paypal">PayPal</option>
            <option value="venmo">Venmo</option>
            <option value="bitcoin">Bitcoin</option>
        </select>
        <button type="button" onclick="showPage(5)">Submit</button>
    </div>
    
    <div id="page5" class="container hidden">
        <h2>Thanks for Subscribing!</h2>
        <p>Your registration has been sent to the head office.</p>
    </div>

    <script>
        function showPage(pageNumber) {
            const pages = document.querySelectorAll('.container');
            pages.forEach(page => page.classList.add('hidden'));
            document.getElementById('page' + pageNumber).classList.remove('hidden');
            
            if (pageNumber === 2) {
                document.getElementById('displayName').innerText = document.getElementById('name').value;
                document.getElementById('displayEmail').innerText = document.getElementById('email').value;
                const profilePicture = document.getElementById('profilePicture').files[0];
                const reader = new FileReader();
                reader.onloadend = function() {
                    document.getElementById('displayProfilePicture').src = reader.result;
                }
                if (profilePicture) {
                    reader.readAsDataURL(profilePicture);
                }
            }
        }
    </script>
</body>
</html>
