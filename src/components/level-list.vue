<template>
    <div class="asideBox">
      <aside>
        <ul class="asideMenu">
          <li v-for="(item,index) in menu" v-bind:key="item.id">
            <div class="oneMenu" @click="myClick(index)" :class="{active: item.isSubShow}">
              <p>{{index+1}}-{{item.name}}
              <span class="switch">+</span>
              </p>              
            </div>
            <ul v-show="item.isSubShow">
              <li v-for="subItem in item.subItems" v-bind:key="subItem.subid">
                <div class="oneMenuChild">{{subItem.name}}</div>
              </li>
            </ul>
          </li>
        </ul>
      </aside>
    </div>
</template>

<script>
 export default {
    props:['menu'],
    data: function () {
  return {
    }
  },
  methods: {
      myClick (index) {
        this.$emit('showsub',index)
      }
    }
}
</script>

<style lang="scss" scoped>
  $menuBackColor:#f1f1f1;
  $menuListH2:#8fbfef;
  .asideBox{
    height: 100%;
    width: 100%;
    aside{
      background: $menuBackColor;
      height: 100%;
      .asideMenu{
        .oneMenu{
          height: 50px;
          line-height: 50px;
          font-size: 18px;
          font-weight: normal;
          color: #454343;
          border-bottom: 1px solid #669cd9;
          .switch{
                cursor: pointer;
                position: absolute;
                right: 30px;                
                width: 10px;
                height: 10px;
          }
        }
        .oneMenuChild{
          padding: 0 20px 0 0;
          height: 40px;
          line-height: 40px;
          background: $menuBackColor;
          border-bottom: 1px solid #ffffff;
          color: #454343;
          font-size: 18px;
        }
        .active {
          background: rgba(93, 93, 233, 0.737);
        }
      }
    }
  }
</style>
