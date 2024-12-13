 <!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadeado com Senha</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        .login-container {
            text-align: center;
            padding: 20px;
            border: 2px solid #ccc;
            border-radius: 10px;
            background-color: #fff;
            width: 300px;
        }
        .login-container input {
            padding: 10px;
            margin: 10px 0;
            width: 200px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .login-container button {
            padding: 10px 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .login-container button:hover {
            background-color: #45a049;
        }
        .error-message {
            color: red;
            display: none;
            font-size: 14px;
            margin-top: 10px;
        }
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            50% { transform: translateX(10px); }
            75% { transform: translateX(-10px); }
            100% { transform: translateX(0); }
        }
        .shake {
            animation: shake 0.3s ease;
        }
        .success-message {
            color: green;
            font-size: 18px;
            display: none;
        }
        .lock-icon {
            font-size: 30px;
            margin-bottom: 20px;
        }
    </style>
</head>
<body>

<div class="login-container">
    <div class="lock-icon">🔒</div>
    <h2>Digite a senha para abrir o cadeado</h2>
    <input type="password" id="password" placeholder="Senha" maxlength="4">
    <button onclick="checkPassword()">Entrar</button>
    <p class="error-message" id="error-message">Senha incorreta! Tente novamente.</p>
    <p class="success-message" id="success-message">Parabéns, você conseguiu, pode abrir a caixa vermelha!</p>
</div>

<script>
    // Defina a senha correta aqui
    const correctPassword = "5225"; // Altere para a senha que você desejar

    function checkPassword() {
        const enteredPassword = document.getElementById('password').value;
        const errorMessage = document.getElementById('error-message');
        const successMessage = document.getElementById('success-message');
        
        if (enteredPassword === correctPassword) {
            errorMessage.style.display = 'none';
            successMessage.style.display = 'block';
        } else {
            successMessage.style.display = 'none';
            errorMessage.style.display = 'block';
            const loginContainer = document.querySelector('.login-container');
            loginContainer.classList.add('shake');
            setTimeout(() => {
                loginContainer.classList.remove('shake');
            }, 300); // Remove a animação após 0.3s
        }
    }
</script>

</body>
</html>
