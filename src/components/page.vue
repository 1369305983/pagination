<template>
    <div class="page">
        <li :class="{'disabled':current == 1}"><a href="#" @click="changePage(current-1)">上一页</a></li>
        <li  v-for = "item in list" :class="{'active':current == item}">
            <a href="#" @click="changePage(item)">{{item}}</a>
        </li>
        <li :class="{'disabled':current == pagenum}"><a href="#" @click="changePage(current+1)">下一页</a></li>
    </div>
</template>

<script>
export default {
    data() {
        return {
            current:this.currentpage
        }
    },
    props:{
        // 总条数
        total:{
            type:Number,
            default:0
        },
        // 当前页面
        currentpage:{
            type:Number,
            default:1
        },
        // 每页显示的数据
        datadisplay:{
            type:Number,
            default:10
        },
        // 显示页码总数
        pagenum:{
            type:Number,
            default:5
        }
    },
    computed:{
        // 页数
        totalpage:function(){
            return Math.ceil(this.total/this.datadisplay);
        },
        list:function() {
            let temp = [];
            let preindex = Math.floor(this.pagenum/2);
            let nextindex = this.pagenum - preindex;
            if(this.current<preindex) {
                for(let i =0;i<this.pagenum;i++){
                    temp.push(i)
                }
            }else if(this.current+nextindex>this.totalpage) {
                for(let i=this.totalpage-this.pagenum;i<this.totalpage;i++) {
                    temp.push(i)
                }
            }else {
                for(let i=this.current-preindex;i<this.current+nextindex;i++) {
                    temp.push(i)
                }
            }
        console.log(temp)
           return temp;
        }
    },
    methods:{
        changePage(val) {
            this.current = val;
        }
    }
}
</script>

<style scoped>
  
  .page {

  }
  li {
      list-style: none;
      color: #323232;
      display: inline-block;
      border-radius: 10px;
      border: 1px solid #ccc;
  }

  li:hover {
      background-color: aqua;
  }

  li a {
      display: inline-block;
      width: 60px;
      height: 30px;
      line-height: 30px;
      text-decoration: none;
      color: #323232;
      cursor: pointer;
  }
  .active {
      background-color: aqua;
  }
</style>
