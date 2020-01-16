<template>
    <div class="child2">
        <h3>我是子组件child2</h3>
        <p>下面是兄弟组件child1传过来的</p>
        <ul>
          <li v-for="item in list">{{item}}</li>
        </ul>
    </div>
</template>

<script>
    import eventBus from '../assets/utils/EventBus'
    export default {
        name: "child2",
        data(){
          return{
            list:[]
          }
        },
        created(){
            this.receive();
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
