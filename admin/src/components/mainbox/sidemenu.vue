<template>
    <el-aside width="$store.state.isCollapse ? '64px' : '240px'">
        <el-menu
        :collapse="$store.state.isCollapse"
        :router="true"
        :default-active="router.fullPath"
        >
        <el-menu-item index="/index">
            <el-icon><HomeFilled/></el-icon>
            <span>首页</span>
        </el-menu-item>

        <el-menu-item index="/center">
            <el-icon><Avatar/></el-icon>
            <span>个人中心</span>
        </el-menu-item>

        <el-sub-menu index="/user-manage" v-admin >
          <template #title>
            <el-icon><UserFilled/></el-icon>
            <span>用户管理</span>
          </template>
            <el-menu-item index="/user/adduser">添加用户</el-menu-item>
            <el-menu-item index="/user/userlist">用户列表</el-menu-item>
        </el-sub-menu>

        <el-sub-menu index="/news-manage ">
          <template #title>
            <el-icon><MessageBox/></el-icon>
            <span>信息管理</span>
          </template>
            <el-menu-item index="/new/addnews">添加信息</el-menu-item>
            <el-menu-item index="/new/newslist">信息列表</el-menu-item>
            <el-menu-item index="/new/noticeBar">通知栏信息</el-menu-item>
        </el-sub-menu>
         
        <el-sub-menu index="/exam-manage ">
          <template #title>
            <el-icon><DocumentRemove/></el-icon>
            <span>考试管理</span>
          </template>
            <el-menu-item index="/exam/addexam">添加考试科目</el-menu-item>
            <el-menu-item index="/exam/examlist">考试科目列表</el-menu-item>
        </el-sub-menu> 

        <el-sub-menu index="/model-manage">
          <template #title>
            <el-icon><Cpu/></el-icon>
            <span>模型管理</span>
          </template>
            <el-menu-item index="/llm/addmodel&modelinfo">模型列表</el-menu-item>
        </el-sub-menu> 
        
        </el-menu>
    </el-aside>
</template>

<script setup>
import { useStore } from 'vuex';
import {HomeFilled,Avatar,UserFilled,MessageBox,DocumentRemove,Cpu} from '@element-plus/icons-vue'
import { useRoute } from 'vue-router';

const router  =useRoute()
const store = useStore()
const  vAdmin = {
    mounted(el){
      if(store.state.userInfo.role!==1){
        el.parentNode.removeChild(el)
      }
    }
}

</script>

<style scoped>
.el-aside{
    height: 100vh; 
    .el-menu{
        height: 100vh;
    }
}
</style>