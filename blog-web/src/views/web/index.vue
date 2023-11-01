<template>
  <div class="body">
    <div class="container">
      <el-container>
        <el-header style="display: flex;">
          <el-menu :default-active="activeIndex2" class="el-menu-demo" mode="horizontal" @select="handleSelect"
            background-color="#545c64" text-color="#fff" active-text-color="#ffd04b" style="display: flex;">
            <h2 class="logo"><b>YiMengLian</b></h2>
            <el-menu-item index="1" class="item">
              <icon class="el-icon-s-home"></icon>首页
            </el-menu-item>
            <el-menu-item index="2" class="item">
              <icon class="el-icon-s-opportunity"></icon>分类
            </el-menu-item>
            <el-menu-item index="3" class="item">
              <icon class="el-icon-discount"></icon>标签
            </el-menu-item>
            <el-menu-item index="4" class="item">
              <icon class="el-icon-wind-power"></icon>归档
            </el-menu-item>
            <el-menu-item index="5" class="item">
              <icon class="el-icon-user"></icon>关于我
            </el-menu-item>

            <el-menu-item index="6" class="item">
              <icon class="el-icon-s-platform"></icon>后台
            </el-menu-item>

            <div class="item sea">
              <div :class="searchFlag == true ? 'open search' : 'search'">
                <input type="search" class="search-box" placeholder="请输入内容" v-model="input3" />
                <span class="search-button" @click="searchFlag = !searchFlag">
                  <span class="search-icon"></span>
                </span>
              </div>


            </div>
            <a href="#" class="menuImg" id="navId" @click="menuFlag = !menuFlag; show = true">
              <img src="../../assets/images/menu.png" class="img">
            </a>
          </el-menu>
        </el-header>
        <div v-show="show">

          <div :class="menuFlag ? 'smallMenu' : 'smallMenuNotshow'">
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-s-home mar-rig"></icon>首页
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-s-opportunity mar-rig"></icon>分类
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-discount mar-rig"></icon>标签
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-wind-power mar-rig"></icon>归档
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-user mar-rig"></icon>关于我
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali">
                <icon class="el-icon-s-platform mar-rig"></icon>后台
              </div>
            </li>
            <li class="menuItem">
              <div class="disandali" style="margin-top: -15px;">
                <div :class="searchFlag == true ? 'open search' : 'search'">
                  <input type="search" class="search-box" placeholder="请输入内容" v-model="input3" />
                  <span class="search-button" @click="searchFlag = !searchFlag">
                    <span class="search-icon"></span>
                  </span>
                </div>
              </div>
            </li>
          </div>
        </div>

        <el-main>
          <div>
            <div class="block">
              <el-carousel trigger="click" class="slideshow">
                <el-carousel-item v-for="i in item" :key="item" >
                  <img :src="i.src" alt="OSS Image" class="slideshowItem">
                </el-carousel-item>
              </el-carousel>
            </div>
          </div>
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </div>


  </div>
</template>

<script>
import OSS from 'ali-oss'

export default {
  components: {},
  props: {},
  data() {
    return {
      client: new OSS({
        region: 'oss-cn-beijing',
        bucket: 'blog-two',
        accessKeyId: 'LTAI5tP29WG81cA2y2cpqC8N',
        accessKeySecret: '5ccPyNnzcARSSXbPkUyjcgCuMEgwDl'
      }),
      item: [
        {src: require('../../assets/images/num_1.png')},
        {src: require('../../assets/images/num_2.png')},
        {src: require('../../assets/images/num_3.png')},
        {src: require('../../assets/images/num_4.png')},
        {src: require('../../assets/images/num_5.png')}
      ],

      searchFlag: false,
      menuFlag: false,
      activeIndex: '1',
      activeIndex2: '1',
      show: false,
      input3: "",
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
    }
  },
  watch: {},
  computed: {
  },
  methods: {},
  created() {
    //从阿里云的oss存储中拿取轮播图的图片 (要付费不用了)
  //   const result = this.client.list({
  //     'max-keys': 1000
  //   });
  //   result.then((data) => {
  //     for (var i = 0; i < data.objects.length; i++) {
  //       if (data.objects[i].name.startsWith("num")) {
  //         this.item.push(this.client.signatureUrl(data.objects[i].name))
  //       } else {
  //       }
  //     }
  //   });
  },
  mounted() { }
};
</script>
<style lang="css" scoped>
.body {
  text-align: center;
}

.disandali {
  display: flex;
  align-items: center;
}

.smallMenuNotshow {
  display: none;
}

.slideshow {
  height: 850px;
}

.slideshowItem {
  width: 100%;
  height: 850px;
}
.el-carousel__item{
  height: 850px;
}
.el-carousel__container{
  height: 850px!important;
}

.el-header {
  padding: 0px;
  height: 60px;
  width: 100%;
}

.el-main {
  padding: 0px;
}


.mar-rig {
  margin-right: 15px;
}


.menuItem {
  animation: slideIn 2s ease-in-out forwards !important;

  display: flex;
  height: 32px;
  margin-top: 13px;
  line-height: 32px;
  padding: 0px 20px;

  font-size: 16px;
  font-weight: bold;
  color: #FFFFFF;
}

.menuItem:hover {
  color: #222;
  background: rgba(255, 255, 255, 0.83);
}

.el-menu {
  padding: 0px 400px;
  width: 100%;
  height: 60px;
}

>>>.el-carousel__arrow{
  top:150%!important;
}

.menuImg {

  display: none;
}

.img {
  width: 25px;
  height: 20px;
}

.container {
  display: flex;

}


.input1 {
  background-color: rgb(84, 92, 100) !important;
  height: 32px;
  line-height: 32px;
  color: #FFFFFF;
  border-radius: 20px;
}

.logo {
  color: #00b5ad;
  font-size: 24px;
  padding: 0px 20px;
}


* {
  box-sizing: border-box;
}

body {
  background: #0e52f0;;
}

.search {
  width: 25px;
  /* 缩小一半 */
  height: 25px;
  /* 缩小一半 */
  margin: 20px auto 0;
  /* 根据需求进行调整 */
  background-color: rgb(84, 92, 100);;
  position: relative;
  overflow: hidden;
  transition:  all .5s ease;;

  &:before {
    content: '';
    display: block;
    width: 1.5px;
    /* 缩小一半 */
    height: 100%;
    position: relative;
    background-color: #00FEDE;
    transition:  all .5s ease;;
  }

  &.open {
    width: 155px;

    /* 缩小一半 */
    &:before {
      height: 25px;
      /* 缩小一半 */
      margin: 5px 0 5px 7.5px;
      /* 根据需求进行调整 */
      position: absolute;
    }
  }
}

.search-box {
  width: 100%;
  /* 占满父元素宽度 */
  height: 100%;
  /* 占满父元素高度 */
  box-shadow: none;
  border: none;
  background: rgb(84, 92, 100);
  color: #fff;
  padding: 5px 25px 5px 11.5px;
  /* 根据需求进行调整 */
  font-size: 10px;

  /* 缩小一半 */
  &:focus {
    outline: none;
  }
}

.search-button {
  width: 25px;
  /* 缩小一半 */
  height: 25px;
  /* 缩小一半 */
  display: block;
  position: absolute;
  right: 0;
  top: 0;
  padding: 5px;
  /* 缩小一半 */
  cursor: pointer;
}

.search-icon {
  width: 10px;
  /* 缩小一半 */
  height: 10px;
  /* 缩小一半 */
  border-radius: 10px;
  /* 缩小一半 */
  border: 1.5px solid #00FEDE;
  display: block;
  position: relative;
  margin-left: 1.25px;
  /* 缩小一半 */
  transition:  all .5s ease;;

  &:before {
    content: '';
    width: 1.5px;
    /* 缩小一半 */
    height: 3.75px;
    /* 缩小一半 */
    position: absolute;
    right: -0.75px;
    /* 缩小一半 */
    top: 7.5px;
    /* 缩小一半 */
    display: block;
    background-color: #00FEDE;
    transform: rotate(-45deg);
    transition:  all .5s ease;;
  }

  &:after {
    content: '';
    width: 1.5px;
    /* 缩小一半 */
    height: 3.75px;
    /* 缩小一半 */
    position: absolute;
    right: -3px;
    /* 缩小一半 */
    top: 10px;
    /* 缩小一半 */
    display: block;
    background-color: #00FEDE;
    transform: rotate(-45deg);
    transition:  all .5s ease;;
  }

  .open & {
    margin: 0;
    width: 15px;
    /* 缩小一半 */
    height: 15px;
    /* 缩小一半 */
    border-radius: 15px;

    /* 缩小一半 */
    &:before {
      transform: rotate(52deg);
      right: 4.5px;
      /* 缩小一半 */
      top: 3.5px;
      /* 缩小一半 */
      height: 4.5px;
      /* 缩小一半 */
    }

    &:after {
      transform: rotate(-230deg);
      right: 4.5px;
      /* 缩小一半 */
      top: 3px;
      /* 缩小一半 */
      height: 4.5px;
      /* 缩小一半 */
    }
  }

}

.el-menu--horizontal>.el-menu-item {
  height: 60px;
}

.icon {
  font-size: 20px;
  margin: 0px 15px;
  cursor: pointer;
}

.sea {
  margin-left: 150px;
}


@media screen and (max-width: 768px) {
  .slideshow {
    height: 400px;
  }
  >>>.el-carousel__arrow{
  top:65%!important;
}
  .slideshowItem {
    width: 100%;
    height: 400px;
  }
  .el-carousel__container{
  height: 400px;
}
  .item {
    display: none;
  }

  .smallMenu {
    height: 320px;
    background-color: rgba(175, 173, 173, 0.831);
    margin-top: -15px;
    animation: slideIn 2s ease-in-out forwards !important;
  }

  @keyframes slideIn {
    0% {
      opacity: 0;

      transform: translateY(-100%);
    }

    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }

  .smallMenuNotshow {
    background-color: rgba(175, 173, 173, 0.831);
    height: 320px;
    display: block;
    animation: slideOut 2s ease-in-out forwards !important;
  }

  @keyframes slideOut {
    0% {
      opacity: 1;

      transform: translateY(0);
    }

    100% {
      opacity: 0;
      display: none;
      transform: translateY(-100%);
    }
  }

  .logo {
    color: #00b5ad;
    font-size: 24px;
    margin-left: -410px;
  }

  .menuImg {
    display: block;
    position: fixed !important;
    right: 20px !important;
    line-height: 70px !important;
  }


}
</style>
