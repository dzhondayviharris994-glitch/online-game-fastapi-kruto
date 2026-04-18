<template>
</head>
<body>
    <nav class="main-nav">
        <a href="index.html">🏠 Главная</a>
        <a href="login.html">🔐 Вход</a>
        <a href="leaders.html">🏆 Лидеры</a>
    </nav>

    <div id="app">
        <h2>Вход в аккаунт</h2>
        <input type="text" v-model="username" placeholder="Имя пользователя (минимум 3 символа)">
        <input type="password" v-model="password" placeholder="Пароль (минимум 4 символа)">
        <div class="error" v-if="errorMessage">{{ errorMessage }}</div>
        <button @click="login">Войти</button>
        <p class="switch-link">
            Нет аккаунта? <a href="register.html">Зарегистрироваться</a>
        </p>
    </div>

    <script>
        const { createApp, ref } = Vue;
        createApp({
            setup() {
                const username = ref('');
                const password = ref('');
                const errorMessage = ref('');

                const validate = () => {
                    if (username.value.length < 3) {
                        errorMessage.value = 'Имя должно быть не менее 3 символов';
                        return false;
                    }
                    if (password.value.length < 4) {
                        errorMessage.value = 'Пароль должен быть не менее 4 символов';
                        return false;
                    }
                    errorMessage.value = '';
                    return true;
                };

                const login = () => {
                    if (validate()) {
                        alert('Добро пожаловать, ' + username.value);
                        // Здесь можно добавить реальный запрос к API
                    }
                };

                return { username, password, errorMessage, login };
            }
        }).mount('#app');
    </script>
</body>
</template