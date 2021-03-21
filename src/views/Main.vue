<template>
    <el-container class = "main_container">
        <!-- 头部布局 -->
        <el-header>
            <!--Logo和项目名称-->
            <div class = "left_box">
                <img src="../assets/img/logo.82b9c7a5.png">
                <span>新冠物资管理系统</span>
            </div>
            <!-- 用户登陆展示的头像 -->
            <div class="right_box">
                <el-dropdown>
                     <img src="../assets/img/logo.82b9c7a5.png">
                     <!-- 下拉菜单 -->
                <el-dropdown-menu slot="dropdown">
                        <el-dropdown-item icon="el-icon-house">系统首页</el-dropdown-item>
                        <el-dropdown-item icon="el-icon-house">交流讨论</el-dropdown-item>
                        <el-dropdown-item icon="el-icon-switch-button">退出登陆</el-dropdown-item>
                    </el-dropdown-menu>
                </el-dropdown>
            </div>
        </el-header>
        <el-container>
            <!-- 侧边栏 -->
    <el-aside width="isCollapse?'60px : '200px'">
                <!--展开或者收起  -->
    <div class="toggle_box" @click="toggleCollapse">|||</div>
 <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#001529"
      text-color="#fff"
      active-text-color="#ffd04b"
      :collapse="isCollapse"
      :collapse-transition = fals
      :unique-opened="true"
      :router="true">
      <MenuTree :menuList = this.menuList></MenuTree>
 </el-menu>
    </el-aside>
        <el-main>Main</el-main>
     </el-container>
    </el-container>
</template>

<script>
import MenuTree from '../components/MenuTree'
export default {
  name: 'Main',
  data () {
    return {
      isCollapse: false
    }
  },
  components: {
    MenuTree
  },
  methods: {
    toggleCollapse () {
      this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="less" scoped>
// 设置整个容器的高度
.main_container{
    height: 100%;
}
// 头部布局
.el-header{
    background-color: #001529;
    display: flex;
    justify-content: space-between;
    color: #FFFFFF;
    padding-left: 0;
    align-content: center;
    font-size: 20px;
// 左边logo和标题
    .left_box{
     display: flex;
     align-items: center;
// logo
     img{
         width: 60px;
         height: 60px;
         margin: 0px 0px 10px 10px
     }
// 标题
     span {
         margin-left: 15px;
     }
    }
    // 右边的登陆头像
    .right_box{
        .el-dropdown>img{
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #FFFFFF;
            margin: 0px,15px, 0px, 0px;
            background-size: contain;
        }
    }
  }
//   侧边栏
  .el-aside {
    background-color: #001529;
    text-align: center;
    .el-menu{
        border-right: none;
    }
    // 展开收起
    .toggle_box{
        background-color: chartreuse;
        color: #333;
        font: size 15px;
        font-weight: bold;
        line-height: 24px;
        color: black;
        letter-spacing: 0.2em;
        text-align: center;
        cursor: pointer;
    }
  }
//   内容主体
  .el-main {
    background-color: #E9EEF3;
    color: #333;
    text-align: center;
    line-height: 160px;
  }
  body > .el-container {
    margin-bottom: 40px;
  }
//   下拉菜单的样式
    .el-dropdown-link {
    cursor: pointer;
    color: #409EFF;
  }
</style>
