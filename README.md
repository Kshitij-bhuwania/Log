<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chaat & Puchka - Customer Login</title>
    <style>
        body { 
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; 
            background: linear-gradient(135deg, #ff7e5f 0%, #feb47b 50%, #ff5722 100%);
            background-size: 200% 200%;
            animation: gradientBG 10s ease infinite;
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            margin: 0; 
        }

        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .auth-container { 
            background: rgba(255, 255, 255, 0.18); 
            backdrop-filter: blur(14px);
            -webkit-backdrop-filter: blur(14px);
            padding: 40px 35px; 
            border-radius: 24px; 
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.15); 
            width: 350px; 
            box-sizing: border-box; 
            border: 1px solid rgba(255, 255, 255, 0.35);
        }

        h2 { 
            text-align: center; 
            color: #ffffff; 
            margin-bottom: 25px; 
            font-weight: 700; 
            letter-spacing: 0.8px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
        }

        input { 
            width: 100%; 
            padding: 14px; 
            margin: 10px 0 20px 0; 
            border: 1px solid rgba(255, 255, 255, 0.4); 
            border-radius: 12px; 
            box-sizing: border-box; 
            font-size: 15px; 
            background: rgba(255, 255, 255, 0.85);
            color: #2d3748;
            transition: all 0.3s ease; 
        }

        input::placeholder {
            color: #718096;
        }

        input:focus { 
            outline: none; 
            border-color: #ffffff; 
            background: rgba(255, 255, 255, 1);
            box-shadow: 0 0 0 4px rgba(255, 255, 255, 0.25);
        }

        button { 
            width: 100%; 
            padding: 14px; 
            background: #d84315; 
            color: white; 
            border: none; 
            border-radius: 12px; 
            font-weight: 700; 
            cursor: pointer; 
            font-size: 16px; 
            letter-spacing: 0.5px;
            box-shadow: 0 6px 20px rgba(216, 67, 21, 0.4);
            transition: all 0.3s ease; 
        }

        button:hover { 
            background: #bf360c; 
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(216, 67, 21, 0.5);
        }

        button:active {
            transform: translateY(0);
        }
    </style>
</head>
<body>

 <div style="text-align: center; position: absolute; top: 12%;">
<img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Chaat Puchka Logo" style="width: 260px; filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));">
</div>

  <div class="auth-container">
        <h2 id="formTitle">Customer Login</h2>
        <input type="text" id="phoneInput" placeholder="Enter Phone Number">
        <button id="authBtn" onclick="handleAuth()">Enter Store</button>
    </div>

<script>
    if (!localStorage.getItem('deliveryCharge')) localStorage.setItem('deliveryCharge', '40');
    if (!localStorage.getItem('categories')) localStorage.setItem('categories', JSON.stringify(['Burger', 'Pizza', 'Beverages']));
    if (!localStorage.getItem('menuItems')) {
        localStorage.setItem('menuItems', JSON.stringify([
            { id: '1', name: 'Cheese Burger', price: 199, category: 'Burger', image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?w=200' },
            { id: '2', name: 'Margherita Pizza', price: 349, category: 'Pizza', image: 'https://images.unsplash.com/photo-1604382355076-af4b0eb60143?w=200' }
        ]));
    }

    function handleAuth() {
        const phone = document.getElementById('phoneInput').value.trim();

        if (!phone) {
            alert('Please enter your phone number.');
            return;
        }

        localStorage.setItem('activeCustomerPhone', phone);
        window.location.href = 'https://kshitij-bhuwania.github.io/Menu/';
    }
</script>
</body>
</html>
