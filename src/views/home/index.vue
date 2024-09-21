<template>
  <div class="home-page-style">
    <div class="top-message">
      <div class="message-item">
        <div class="avatar-box">
          <img src="@/assets/home/avatar.jpg" alt="" />
        </div>
        <div class="personal-name-img">
          <img src="@/assets/home/name.png" alt="" />
        </div>
      </div>
      <div class="message-detail-item">
        <div class="title-box">邮箱：</div>
        <div class="detail-box">wlw7890000@163.com</div>
      </div>
      <div class="message-detail-item">
        <div class="title-box">个人简介：</div>
        <div class="detail-box">
          Good morning, and in case I don't see you, good afternoon, good evening, and good night!
        </div>
      </div>
    </div>
    <div class="project-box">
      <div class="title-name">个人项目展示</div>
      <div class="project-content-box">
        <el-row :gutter="10">
          <el-col v-for="item in state.projectList" :key="item.id">
            <div class="card-box-style" @click="toPath(item.url)">
              <el-card shadow="hover">
                <div class="card-item-style">
                  <div class="project-img">
                    <img :src="item.img" alt="" />
                    <!--                    <img src="@/assets/home/platform.png" alt="" />-->
                  </div>
                  <div class="message-box">{{ item.projectName }}</div>
                </div>
              </el-card>
            </div>
          </el-col>
        </el-row>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue"
import platform from "@/assets/home/platform.png"
import solar_system from "@/assets/home/solar_system.jpg"
import { ElMessage } from "element-plus"

const state = reactive({
  projectList: [
    {
      id: "0",
      projectName: "基于vue3+threejs实现太阳系与奥尔特云层",
      img: solar_system,
      url: "https://www.psophora.com:449/zihuai/"
    },
    {
      id: "1",
      projectName: "数据中台",
      img: platform,
      url: "https://www.psophora.com:449/platform/"
    },
    {
      id: "2",
      projectName: "数据中台",
      img: "",
      url: ""
    },
    {
      id: "4",
      projectName: "数据中台",
      img: "",
      url: ""
    },
    {
      id: "5",
      projectName: "数据中台",
      img: "",
      url: ""
    }
  ]
})

const toPath = (url) => {
  if (!url) {
    ElMessage({
      type: "warning",
      message: "暂未部署，请联系博主"
    })
    return false
  }
  window.open(url, "_blank")
}
</script>

<style lang="scss" scoped>
.home-page-style {
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-color: #fff;
  padding: 20px;
  @include flex-column-start;
  .top-message {
    width: 100%;
    .message-item {
      width: 100%;
      @include flex-left;
      margin-bottom: 30px;
      .avatar-box {
        width: 60px;
        height: 60px;
        border-radius: 50%;
        overflow: hidden;
        margin-top: 12px;
        img {
          width: 100%;
          height: 100%;
        }
      }
      .personal-name {
        width: 60px;
        height: 60px;
        img {
          width: 100%;
          height: 100%;
        }
      }
    }
    .message-detail-item {
      width: 100%;
      padding: 0 50px;
      @include flex-left-center;
      margin-top: 10px;
      font-size: 18px;
      color: #333;
    }
  }
  .project-box {
    flex: 1;
    height: 0;
    overflow-y: auto;
    margin-top: 30px;
    @include flex-column-start;
    .title-name {
      font-size: 22px;
      font-weight: 600;
      color: #333;
    }
    .project-content-box {
      flex: 1;
      overflow-y: auto;
      //overflow-x: hidden;
      //padding: 0 5px;
      margin: 10px 0;

      .card-box-style {
        margin-bottom: 10px;

        .card-item-style {
          //overflow: hidden;
          cursor: pointer;
          height: 0;
          padding-bottom: 57%;
          @include flex-column-start-center;
          .project-img {
            width: calc(100% - 30px);
            height: 0;
            padding-bottom: calc(57% - 48px);
            border-radius: 5px;
            margin-top: 10px;
            img {
              width: 100%;
              border-radius: 5px;
              transition: all 0.1s linear;
            }
          }
          .message-box {
            line-height: 40px;
            color: #333;
            font-size: 18px;
          }
        }

        .card-item-style:hover {
          .message-box {
            color: #409eff;
          }
          img {
            transform: scale(1.01);
          }
        }
      }
    }
  }
}

// 隐藏滚动条
::-webkit-scrollbar {
  display: none;
}

@media screen and (min-width: 1600px) {
  .el-col {
    max-width: 25%;
    width: 25%;
    flex: 0 0 25%;
  }
}

@media screen and (min-width: 1000px) and (max-width: 1600px) {
  .el-col {
    max-width: 33.33%;
    width: 33.33%;
    flex: 0 0 33.33%;
  }
}

@media screen and (min-width: 500px) and (max-width: 1000px) {
  .el-col {
    max-width: 50%;
    width: 50%;
    flex: 0 0 50%;
  }
}

@media only screen and (max-width: 500px) {
  .el-col {
    max-width: 100%;
    width: 100%;
    flex: 0 0 100%;
  }
}
</style>
