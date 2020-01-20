<template>
    <div class="child2">
        <h3>{{msg}}</h3>
        <p>下面是兄弟组件child1传过来的</p>
        <ul>
          <li v-for="item in list">{{item}}</li>
        </ul>
        <p>通过this.$root获取父组件的数据</p>
    </div>
</template>

<script>
    import eventBus from '../assets/utils/EventBus'
    export default {
        name: "child2",
        data(){
          return{
            list:[],
            msg:'我是子组件child2'
          }
        },
        created(){
            this.receive();
            //console.log('======',this.$root)
        },
        methods:{
          receive(){
            eventBus.$on('mFun',(data) => {
              this.list.push(data);
            })
          }
        }
    }
</script>

<style scoped>
  .child2{
    margin-top: 10px;
    border: 1px solid blue;
  }
</style>
