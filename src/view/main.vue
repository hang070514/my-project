<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>{{str}}</p>
    <child1 :list="list" :obj="obj" @mFun="getMsg" :change="change"></child1>
    <child2></child2>
  </div>
</template>

<script>
import child1 from '../components/child1'
import child2 from '../components/child2'
export default {
  name: 'Main',
  components:{
    child1,
    child2
  },
  data () {
    return {
      msg: 'Hello 我是父组件',
      str:'改变之前',
      obj:{
        name:'zhang'
      },
      list:[
        'vue','react','angular'
      ]
    }
  },
  methods:{
    getMsg(res){
      this.str = res;
    },
    change(){
      this.str = 'str改变了';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
