<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chaat & Puchka - Customer Login</title>
    <style>
        body { 
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; 
            background: linear-gradient(135deg, #fff5f0 0%, #ffe3db 100%); 
            display: flex; 
            justify-content: center; 
            align-items: center; 
            height: 100vh; 
            margin: 0; 
        }
        .auth-container { 
            background: #ffffff; 
            padding: 35px; 
            border-radius: 20px; 
            box-shadow: 0 12px 30px rgba(211, 84, 0, 0.12); 
            width: 340px; 
            box-sizing: border-box; 
            border: 2px solid #fde8e4;
        }
        h2 { 
            text-align: center; 
            color: #b5370a; 
            margin-bottom: 25px; 
            font-weight: 700; 
            letter-spacing: 0.5px;
        }
        input { 
            width: 100%; 
            padding: 12px; 
            margin: 10px 0 18px 0; 
            border: 1px solid #f5c6bb; 
            border-radius: 10px; 
            box-sizing: border-box; 
            font-size: 14px; 
            background-color: #fff9f8;
            transition: all 0.2s; 
        }
        input:focus { 
            outline: none; 
            border-color: #e65100; 
            background-color: #fff;
            box-shadow: 0 0 0 3px rgba(230, 81, 0, 0.1);
        }
        button { 
            width: 100%; 
            padding: 12px; 
            background: linear-gradient(135deg, #f4511e 0%, #d84315 100%); 
            color: white; 
            border: none; 
            border-radius: 10px; 
            font-weight: 600; 
            cursor: pointer; 
            font-size: 15px; 
            box-shadow: 0 4px 12px rgba(216, 67, 21, 0.3);
            transition: all 0.2s; 
        }
        button:hover { 
            background: linear-gradient(135deg, #d84315 0%, #bf360c 100%); 
            box-shadow: 0 6px 15px rgba(216, 67, 21, 0.4);
        }
    </style>
</head>
<body>

 <div style="text-align: center;">
<img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Chaat Puchka Logo" style="width: 300px;">
</div>
  <br>
  <br><br><br>
  <div class="auth-container">
        <h2 id="formTitle">Spicy Customer Login</h2>
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

        // Save active customer phone and redirect directly to menu
        localStorage.setItem('activeCustomerPhone', phone);
        window.location.href = 'https://kshitij-bhuwania.github.io/Menu/';
    }
</script>
</body>
</html>
