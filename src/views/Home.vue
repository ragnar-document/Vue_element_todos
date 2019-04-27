<template>
  <div>
    <h1>vue_ele_todos</h1>
    <el-container>
      <el-header>
        <el-input
          placeholder="请输入内容"
          @change="addTodos()"
          v-model="input"
          clearable
          >
        </el-input>
      </el-header>
      <el-main>
        <ul>
          <li v-bind:class="[item.judge ? 'active' : '', 'addline']" v-for="item in todos" :key="item.id" >
            <input class="el-option" type="checkbox"  v-model="item.judge"  @click="switchover(item)">
            {{item.text}}
            <p class="remove" @click="removeOnce(item)">X</p>
          </li>
        </ul>
      </el-main>
      <el-footer>
        <input class="allCheckbox" type="checkbox">
        <ul>
          <!-- <li><a href="/">全部</a></li>
          <li><a href="/">待办/a></li>
          <li><a href="/">已办</a></li> -->
        </ul>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: '',
      radio: '',
      todos:[{
        id: 1,
        text: '测试一',
        judge: false,
      },{
        id: 2,
        text: '测试二',
        judge: true
      }]
    }
  },
  methods:{
    addTodos:function(){
      let value = this.input
      if (!value) {
        return
      }
      this.todos.push({id:this.todos.length + 1,text:value})
      this.input = ''
    },
    removeOnce:function (item) {
      let index =this.todos.indexOf(item)
      this.todos.splice(index,1)
    },
    switchover:function(item){
      let judge = item.judge;
      judge =  !judge;
    }
  }
}
</script>

<style>
h1{
  color: #fff;
}
li{
  list-style: none
}
.el-container{
  margin: 0 auto;
  width: 500px;;
  background: #fff;
  border-radius: 20px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, .2), 0 0 6px rgba(0, 0, 0, .04)
}
.el-container .el-header{
  position: relative;
  border-bottom: 1px solid rgba(0, 0, 0, .2);
}
.el-container .el-main{
  border-bottom: 1px solid rgba(0, 0, 0, .2);
}
.el-input--suffix{
  height: 100%;
  line-height: 4;
}
.el-container .el-header .el-input__inner{
  border: none
}
.el-option{
  position: absolute;
  top: 5px;
  left: 5px;
  float: left;
  height: 20px;
  width: 20px;
}
.addline{
  position: relative;
  line-height: 30px;
  border-bottom: 1px solid #4997e4;
  margin-bottom: 10px;
  padding-left: 30px;
  text-align: left;
}
.addline.active{
  background: #4997e4;
  color: #fff;
  border-top-right-radius: 8px;
  border-top-left-radius: 8px;
  transition: all ease 0.2s;
}
.addline:hover .remove{
  color: #4997e4;
}

.remove{
  float: right;
  padding: 5px;
  width: 10px;
  height: 10px;
  margin: auto 0;
  font-size: 16px;
  color: #fff;
  transition: color 0.2s ease-out;
  cursor: pointer;
}
.allCheckbox{

}
</style>
