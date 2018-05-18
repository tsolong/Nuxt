<template>
    <div>
        <nuxt-link to="/">回到首页</nuxt-link>
        <ol>
            <li v-for="(item, i) in province" :index="i">{{item.code}}　{{item.name}}　{{item.url}}</li>
        </ol>
    </div>
</template>

<script>

    import axios from 'axios';

    export default {
        asyncData() {
            return axios.get("http://www.nmc.cn/f/rest/province")
                .then((res) => {
                    console.log('ajax request success');
                    console.log(res.data.length);
                    return {province: res.data}
                })
                .catch((e) => {
                    console.error('ajax request fail');
                    console.error(e);
                });
        },
        head: {
            title: '关于我们'
        }
    }
</script>