<template>
    <div class="login">

        <form @submit.prevent="onLogin">

            <input name="email" v-model="email" class="form-control" placeholder="email">
            <input name="password" v-model="password" class="form-control" placeholder="password">

            <button type="submit">
                Авторизоваться
            </button>

        </form>

    </div>
</template>

<script>


    import axios from 'axios'

    export default {

        name: 'Login',

        data() {
            return {
                password: '',
                email: ''
            }
        },
        methods: {
            onLogin() //Авторизация. Доделать (добавить проверки, сделать более аккуратный код)
            {
                var error = false;

                if (!this.email.trim()) {
                    error = true;
                }

                if (!this.password.trim()) {
                    error = true;
                }

                if (!error) {
                    axios
                        .post('http://127.0.0.1:8000/api/login?email=' + this.email + '&password=' + this.password)
                        //     .get('http://127.0.0.1:8000/api/users?jwt=' + localStorage.getItem('jwt'))

                        .then(response => {

                            if (response.data.result) {
                                var jwt = response.data.params.jwt;
                                localStorage.setItem('jwt', jwt); // Сохраняем токен, если все ок
                            }

                        })
                }


            }
        }


    }

</script>
