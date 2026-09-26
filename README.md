<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Customer Portal - Login / Register</title>
    <style>
        body { font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; -webkit-font-smoothing: antialiased; background: #f0f2f5; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .auth-container { background: white; padding: 35px; border-radius: 12px; box-shadow: 0 4px 16px rgba(0,0,0,0.08); width: 320px; }
        h2 { text-align: center; color: #1a1a1a; margin-bottom: 24px; font-weight: 600; }
        input { width: 100%; padding: 12px; margin: 10px 0; border: 1px solid #d1d5db; border-radius: 8px; box-sizing: border-box; font-size: 14px; outline: none; transition: border-color 0.2s; }
        input:focus { border-color: #ff4757; }
        button { width: 100%; padding: 12px; background: #ff4757; color: white; border: none; border-radius: 8px; font-weight: 600; cursor: pointer; margin-top: 12px; font-size: 15px; transition: background 0.2s; }
        button:hover { background: #ff6b81; }
        .switch-text { text-align: center; margin-top: 20px; font-size: 14px; color: #4b5563; cursor: pointer; }
        .switch-text span { color: #ff4757; font-weight: 600; }
    </style>
</head>
<body>

<div class="auth-container">    
  <h2 id="formTitle">Customer Register</h2>
        <input type="text" id="phoneInput" placeholder="Enter Phone Number">
        <input type="password" id="passInput" placeholder="Enter Password">
        <button id="authBtn" onclick="handleAuth()">Register</button>
        
   <div class="switch-text" onclick="toggleMode()">
            <span id="switchLabel">Already have an account? Login here</span>
        </div>
    </div>

<script>
    let isLoginMode = false;

    if (!localStorage.getItem('deliveryCharge')) localStorage.setItem('deliveryCharge', '40');
    if (!localStorage.getItem('categories')) localStorage.setItem('categories', JSON.stringify(['Burger', 'Pizza', 'Beverages']));
    if (!localStorage.getItem('menuItems')) {
        localStorage.setItem('menuItems', JSON.stringify([
            { id: '1', name: 'Cheese Burger', price: 199, category: 'Burger', image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?w=200' },
            { id: '2', name: 'Margherita Pizza', price: 349, category: 'Pizza', image: 'https://images.unsplash.com/photo-1604382355076-af4b0eb60143?w=200' }
        ]));
    }

    function toggleMode() {
        isLoginMode = !isLoginMode;
        document.getElementById('formTitle').innerText = isLoginMode ? 'Customer Login' : 'Customer Register';
        document.getElementById('authBtn').innerText = isLoginMode ? 'Login' : 'Register';
        document.getElementById('switchLabel').innerText = isLoginMode ? "Don't have an account? Register" : "Already have an account? Login here";
    }

    function handleAuth() {
        const phone = document.getElementById('phoneInput').value.trim();
        const pass = document.getElementById('passInput').value.trim();

        if (!phone || !pass) {
            alert('Please enter both phone number and password.');
            return;
        }

        let users = JSON.parse(localStorage.getItem('users') || '{}');

        if (!isLoginMode) {
            if (users[phone]) {
                alert('Phone number already registered! Please log in.');
                return;
            }
            users[phone] = { password: pass };
            localStorage.setItem('users', JSON.stringify(users));
            
            alert('Registration successful! Please login with your credentials.');
            toggleMode();
            document.getElementById('phoneInput').value = phone;
            document.getElementById('passInput').value = '';
        } else {
            if (!users[phone] || users[phone].password !== pass) {
                alert('Invalid phone number or password.');
                return;
            }
            localStorage.setItem('activeCustomerPhone', phone);
            window.location.href ='https://kshitij-bhuwania.github.io/Menu/';
        }
    }
</script>
</body>
</html>
