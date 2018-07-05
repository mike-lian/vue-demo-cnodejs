<template>
    <div>
        <Header></Header>
        <div class="article_list">
            <ul>
                <li v-for="i in list">
                    <time v-text="$utils.goodTime(i.create_at)"></time>  
                    <router-link :to="'/content/'+ i.id">
                        {{i.title}}
                    </router-link>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import Header from '../components/header'
import Footer from '../components/footer'
export default {
    components: {
        Header,Footer
    },
    data() {
        return {
            list: []
        }
    },
    created() {
        this.getData();
        console.log(this.$route)
    },
    methods: {
        getData() {
            this.$api.get('topics',null,r=>{
                this.list = r.data
            })
        }
    }
}
</script>

