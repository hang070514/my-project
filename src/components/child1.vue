<template>
  <div class="child1">
    <h3>我是子组件child1</h3>
    <p>下面是父组件传过来的数组:</p>
    <ul>
      <li v-for="(item,index) in list">{{item}}</li>
    </ul>
    <p>父组件传过来的:{{obj.name}}</p>
    <p>
      <button @click="sendToParent">点击改变父组件的值</button>
    </p>
    <p>
      <input type="text" v-model="message">
      <button @click="sendToChild2">向子组件child2传值</button>
    </p>
  </div>

</template>

<script>
  import eventBus from '../assets/utils/EventBus'
    export default {
        name: "child1",
        props:{
          obj:{
            type:Object,
            default:() => {
              return {
                name:''
              }
            }
          },
          list:{
            type:Array,
            default: () => {
              return []
            }
          },
          change:Function
        },
      data(){
          return {
            message:'',
            list1:[
            ]
          }
      },
      methods:{
        sendToParent(){
            this.$emit('mFun','改变之后')
            //this.change();
        },
        sendToChild2(){
          //this.list1.push(this.message)
          eventBus.$emit('mFun',this.message)
        }
      }
    }
</script>

<style scoped>
  .child1{
    border: 1px solid red;
  }
</style>
