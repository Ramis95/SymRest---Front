<template>
    <div class="info">
        <h1>Main info</h1>
        <div class="block">
            123123123
        </div>


    </div>
</template>

<script>

    import axios from 'axios'

    export default {

        data() {
            return {
                info: null,
                api_response: false
            }
        },
        mounted() {
            axios
                // .post('http://127.0.0.1:8000/api/registration?email="ads@adas.ru"')
                // .then(response => {
                //     this.info = response;
                //     this.showInfo();
                // })
        },
        methods: {
            showInfo() {
                console.log(document.cookie);
                console.log(this.info.data);
            }
        }
    }

</script>
