<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chaat & Puchka - Customer Login</title>
    <style>
        body { 
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; 
            background: linear-gradient(135deg, #ff6a00 0%, #ee0979 100%);
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            margin: 0; 
            position: relative;
            overflow: hidden;
        }

        /* Subtle floating street food pattern overlay */
        body::before {
            content: "";
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background-image: radial-gradient(rgba(255, 255, 255, 0.15) 2px, transparent 2px);
            background-size: 30px 30px;
            pointer-events: none;
        }

        .auth-container { 
            background: rgba(255, 255, 255, 0.15); 
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            padding: 40px 35px; 
            border-radius: 24px; 
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2); 
            width: 350px; 
            box-sizing: border-box; 
            border: 1px solid rgba(255, 255, 255, 0.3);
            z-index: 2;
        }

        h2 { 
            text-align: center; 
            color: #ffffff; 
            margin-bottom: 25px; 
            font-weight: 700; 
            letter-spacing: 0.8px;
            text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        input { 
            width: 100%; 
            padding: 14px; 
            margin: 10px 0 20px 0; 
            border: 1px solid rgba(255, 255, 255, 0.4); 
            border-radius: 12px; 
            box-sizing: border-box; 
            font-size: 15px; 
            background: rgba(255, 255, 255, 0.9);
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
            background: #ff5722; 
            color: white; 
            border: none; 
            border-radius: 12px; 
            font-weight: 700; 
            cursor: pointer; 
            font-size: 16px; 
            letter-spacing: 0.5px;
            box-shadow: 0 6px 20px rgba(255, 87, 34, 0.4);
            transition: all 0.3s ease; 
        }

        button:hover { 
            background: #f4511e; 
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255, 87, 34, 0.6);
        }

        button:active {
            transform: translateY(0);
        }
    </style>
</head>
<body>

 <div style="text-align: center; position: absolute; top: 10%; z-index: 2;">
<img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Chaat & Puchka Logo" style="width: 260px; filter: drop-shadow(0 4px 10px rgba(0,0,0,0.2));">
</div>

  <div class="auth-container">
        <h2 id="formTitle">Customer Login</h2>
        <input type="text" id="phoneInput" placeholder="Enter Phone Number">
        <button id="authBtn" onclick="handleAuth()">Login</button>
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
