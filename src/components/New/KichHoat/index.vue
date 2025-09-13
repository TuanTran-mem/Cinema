<template>
    <div>
        aaaaaa
    </div>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            hash_reset : this.$route.params.hash_reset,
        }
    },
    mounted() {
        this.kichHoat();
    },
    methods: {
        kichHoat(){
            var payload = {
                hash : this.hash_reset
            };
            axios
                .post("http://127.0.0.1:8000/api/kich-hoat", payload)
                .then((res) => {
                    if(res.data.status){
                        this.$toast.success(res.data.message);
                        this.$router.push('/new-dang-nhap');
                    }
                    else{
                        this.$toast.error(res.data.message);
                    }
                });
        }
    },
}
</script>
<style>
    
</style>