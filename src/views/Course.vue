<template>
    <div class="about">
        <h1>这是课程页面</h1>
        <button @click="test">点我</button>
        <p>
            <button @click="data1">得数据</button>
        </p>
        <p>
            <button @click="data2">发送post请求</button>
        </p>
        <p>{{course}}</p>
        <p>{{msgs}}</p>
    </div>

</template>

<script>
    export default {

        data: function () {
            return {
                course: ['treadf'],
                msgs:''
            }
        },
        methods: {
            test: function () {
                alert('test')
            },
            data1: function () {
                let _this = this
                this.$axios.request({
                    url: _this.$url + 'test/',
                    method: 'get'
                }).then(function (response) {
                    _this.course = response.data
                }).catch(function (response) {
                    console.log(response)
                })

            },
            data2: function () {
                let _this = this
                _this.$axios.request({
                    url: _this.$url + 'test/',
                    method: 'post',
                    data: {'vue': '我是vue传过来的数据'},
                }).then(function (response) {
                    _this.msgs = response.data
                }).catch(function (response) {
                    _this.msgs = response.data
                })
            }
        }
    }
</script>

<style scoped>

</style>