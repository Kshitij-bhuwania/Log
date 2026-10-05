<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Customer Portal - Login / Register</title>
    <style>
        body { font-family: 'Segoe UI', system-ui, -apple-system, sans-serif; background: white; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; }
        .auth-container { background: white; padding: 35px; border-radius: 16px; box-shadow: 0 10px 25px rgba(0,0,0,0.05); width: 340px; box-sizing: border-box; }
        h2 { text-align: center; color: #1a202c; margin-bottom: 25px; font-weight: 600; }
        input { width: 100%; padding: 12px; margin: 10px 0 18px 0; border: 1px solid #e2e8f0; border-radius: 8px; box-sizing: border-box; font-size: 14px; transition: border 0.2s; }
        input:focus { outline: none; border-color: #ff4757; }
        button { width: 100%; padding: 12px; background: #ff4757; color: white; border: none; border-radius: 8px; font-weight: 600; cursor: pointer; font-size: 14px; transition: background 0.2s; }
        button:hover { background: #ff6b81; }
        .switch-text { text-align: center; margin-top: 15px; font-size: 13px; color: #718096; cursor: pointer; }
        .switch-text span { color: #ff4757; font-weight: 600; }
        .forgot-text { text-align: right; margin-top: -10px; margin-bottom: 15px; font-size: 12px; color: #718096; cursor: pointer; }
        .forgot-text span { color: #ff4757; }
    </style>
</head>
<body>

 <div style="text-align: center;">
<img src="https://i.postimg.cc/SsSZBQ9q/1000037254-removebg-preview.png" alt="Description" style="width: 300px;">
</div>
  <br>
  <br><br><br>
  <div class="auth-container">
        <h2 id="formTitle">Customer Register</h2>
        <input type="text" id="phoneInput" placeholder="Enter Phone Number">
        <input type="password" id="passInput" placeholder="Enter Password">
        <input type="password" id="newPassInput" placeholder="Enter New Password" style="display: none;">
        <button id="authBtn" onclick="handleAuth()">Register</button>
        
        <div id="forgotSection" class="forgot-text" style="display: none;" onclick="toggleForgotMode()">
            <span>Forgot Password?</span>
        </div>

        <div class="switch-text" onclick="toggleMode()">
            <span id="switchLabel">Already have an account? Login here</span>
        </div>
    </div>

<script>
    let mode = 'register'; // 'register', 'login', 'forgot'

    if (!localStorage.getItem('deliveryCharge')) localStorage.setItem('deliveryCharge', '40');
    if (!localStorage.getItem('categories')) localStorage.setItem('categories', JSON.stringify(['Burger', 'Pizza', 'Beverages']));
    if (!localStorage.getItem('menuItems')) {
        localStorage.setItem('menuItems', JSON.stringify([
            { id: '1', name: 'Cheese Burger', price: 199, category: 'Burger', image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?w=200' },
            { id: '2', name: 'Margherita Pizza', price: 349, category: 'Pizza', image: 'https://images.unsplash.com/photo-1604382355076-af4b0eb60143?w=200' }
        ]));
    }

    function toggleMode() {
        const title = document.getElementById('formTitle');
        const btn = document.getElementById('authBtn');
        const switchLabel = document.getElementById('switchLabel');
        const forgotSection = document.getElementById('forgotSection');
        const newPassInput = document.getElementById('newPassInput');
        const passInput = document.getElementById('passInput');

        newPassInput.style.display = 'none';

        if (mode === 'register') {
            mode = 'login';
            title.innerText = 'Customer Login';
            btn.innerText = 'Login';
            switchLabel.innerText = "Don't have an account? Register";
            forgotSection.style.display = 'block';
            passInput.placeholder = 'Enter Password';
        } else {
            mode = 'register';
            title.innerText = 'Customer Register';
            btn.innerText = 'Register';
            switchLabel.innerText = 'Already have an account? Login here';
            forgotSection.style.display = 'none';
            passInput.placeholder = 'Enter Password';
        }
    }

    function toggleForgotMode() {
        mode = 'forgot';
        document.getElementById('formTitle').innerText = 'Reset Password';
        document.getElementById('authBtn').innerText = 'Update Password';
        document.getElementById('forgotSection').style.display = 'none';
        document.getElementById('switchLabel').innerText = 'Back to Login';
        document.getElementById('passInput').placeholder = 'Enter Existing Password (or leave blank)';
        document.getElementById('newPassInput').style.display = 'block';
    }

    function handleAuth() {
        const phone = document.getElementById('phoneInput').value.trim();
        const pass = document.getElementById('passInput').value.trim();
        const newPass = document.getElementById('newPassInput').value.trim();

        if (!phone) {
            alert('Please enter your phone number.');
            return;
        }

        let users = JSON.parse(localStorage.getItem('users') || '{}');

        if (mode === 'register') {
            if (!pass) {
                alert('Please enter a password.');
                return;
            }
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
        } else if (mode === 'login') {
            if (!pass) {
                alert('Please enter your password.');
                return;
            }
            if (!users[phone] || users[phone].password !== pass) {
                alert('Invalid phone number or password.');
                return;
            }
            localStorage.setItem('activeCustomerPhone', phone);
            window.location.href = 'https://kshitij-bhuwania.github.io/Menu/';
        } else if (mode === 'forgot') {
            if (!newPass) {
                alert('Please enter a new password.');
                return;
            }
            if (!users[phone]) {
                alert('Phone number not found. Please register first.');
                return;
            }
            
            users[phone].password = newPass;
            localStorage.setItem('users', JSON.stringify(users));
            alert('Password reset successful! Please login with your new password.');
            
            // Switch back to login state
            document.getElementById('newPassInput').value = '';
            document.getElementById('passInput').value = '';
            toggleMode();
            document.getElementById('phoneInput').value = phone;
        }
    }
</script>
</body>
</html>
