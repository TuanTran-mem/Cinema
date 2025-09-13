<template>
    <table class="table table-hover table-bordered">
        <thead>
            <tr>
                <th>refNo</th>
                <th>transactionDate</th>
                <th>creditAmount</th>
                <th>description</th>
            </tr>
        </thead>
        <tbody>
            <template v-for="(item, index) in list_giao_dich" :key="index">
                <tr>
                    <td>{{ item.refNo }}</td>
                    <td>{{ item.transactionDate }}</td>
                    <td>{{ item.creditAmount }}</td>
                    <td>{{ item.description }}</td>
                </tr>
            </template>
        </tbody>
    </table>
</template>
<script>
import axios from 'axios';

export default {
    data() {
        return {
            list_giao_dich: [],
        }
    },
    mounted() {
        this.loadGiaoDich();
    },
    methods: {
        loadGiaoDich() {
            const payload = {
                "USERNAME": "0393888560",
                "PASSWORD": "TranTuan23803@",
                "DAY_BEGIN": "09/07/2025",
                "DAY_END": "10/07/2025",
                "NUMBER_MB": "0393888560"
            };
            axios
                .post("https://api-mb.dzmid.io.vn/api/transactions", payload)
                .then((res) => {
                    this.list_giao_dich = res.data.data.transactionHistoryList;
                })
        }
    },
}
</script>
<style></style>