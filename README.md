<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Customer Portal - Login</title>
    <style>
        body { font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; background: white; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .auth-container { background: white; padding: 35px; border-radius: 16px; box-shadow: 0 10px 25px rgba(0,0,0,0.05); width: 340px; box-sizing: border-box; }
        h2 { text-align: center; color: #1a202c; margin-bottom: 25px; font-weight: 600; }
        input { width: 100%; padding: 12px; margin: 10px 0 18px 0; border: 1px solid #e2e8f0; border-radius: 8px; box-sizing: border-box; font-size: 14px; transition: border 0.2s; }
        input:focus { outline: none; border-color: #ff4757; }
        button { width: 100%; padding: 12px; background: #ff4757; color: white; border: none; border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 14px; transition: background 0.2s; }
        button:hover { background: #ff6b81; }
    </style>
</head>
<body>

 <div style="text-align: center;">
<img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Description" style="width: 300px;">
</div>
  <br>
  <br><br><br>
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

        // Save active customer phone and redirect directly to menu
        localStorage.setItem('activeCustomerPhone', phone);
        window.location.href = 'https://kshitij-bhuwania.github.io/Menu/';
    }
</script>
</body>
</html>
