<template>
  <div id="app">
    <div class="header">已打开<span >{{chooseName}}</span>列表</div>
    <myLevelList :menu="menuList" v-on:showsub="showToggle" ></myLevelList>
  </div>
</template>

<script>
import myLevelList from './components/level-list.vue'

export default {
  data(){
      return{

        menuList:[
          {
            name:'策略名称',
            isSubShow:false,
            subItems:[
              {name:'账号爆破防护'},
              {name:'API防护'},
              {name:'网络爬虫放行'},
            ]
          },
          {
            name:'匹配类型',
            isSubShow:false,
            subItems:[
              {name:'基础'},
              {name:'自定义'},
            ]
          },
          {
            name:'匹配字段',
            isSubShow:false,
            subItems:[
              {name:'Cookie'},
              {name:'Referer'},
              {name:'HTTP-Method'},
              {name:'User-Agent'},
              {name:'X-Forwarded-For'},
              {name:'URI'},
            ]
          },
          {
            name:'逻辑符',
            isSubShow:false,
            subItems:[
              {name:'包含'},
              {name:'不包含'},
              {name:'等于'},
              {name:'不等于'},
              {name:'长度小于'},
              {name:'长度等于'},
            ]
          },
          {
            name:'匹配动作',
            isSubShow:false,
            subItems:[
              {name:'阻断'},
              {name:'放行'},
              {name:'记录'},
              {name:'JS挑战'},
              {name:'验证码'}, 
            ]
          },
          {
            name:'优先级',
            isSubShow:false,
            subItems:[
              {name:'1'},
              {name:'2'},
              {name:'3'},
              {name:'4'},
              {name:'5'},  
            ]
          },
          {
            name:'生效端口',
            isSubShow:false,
            subItems:[
              {name:'1'},
              {name:'443'},
              {name:'8080'},
            ]
          },
        ],
      }
    },
  name: 'App',
  components: {
    myLevelList
  },
  methods:{
  // 点击展开折叠菜单事件
    showToggle:function(index){
    this.menuList[index].isSubShow = !this.menuList[index].isSubShow;
    },
  },
  computed:{
    chooseName:function(){
      let newlist=this.menuList.filter(r=>{
        if(r.isSubShow) return true
      })
      let namelist=newlist.filter(()=>{
        return namelist.name !== ''
      })
      console.log(namelist.name)
      return "";
      // return newlist 
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.header{
  text-align: left;
  font-size: 10px;
}

</style>
