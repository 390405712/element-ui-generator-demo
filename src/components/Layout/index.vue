<template>
  <!-- style="--el-color-primary: #294cff" -->
  <div class="Layout">
    <div class="header">
      <div class="logo-container">
        <div class="logo"></div>
        <div class="title">项目脚手架</div>
      </div>
    </div>
    <div class="content">
      <div class="left">
        <el-menu router :default-active="$route.path" :collapse="collapse">
          <template v-for="(item, index) in $router.options.routes" :index="item.path">
            <el-submenu v-if="item.children" :key="item.path" :index="item.path">
              <template #title>
                <!-- <el-icon>
                    <i :class="`iconfont ${icons[item.name?.split('?')[0]]}`"></i>
                  </el-icon> -->
                {{ item.name?.split('?')[0] }}
              </template>
              <el-menu-item-group>
                <template v-for="(childItem, index) in item.children">
                  <el-menu-item :key="index" :index="childItem.path" v-if="!childItem.name.includes('hidden')">
                    {{ childItem.name?.split('?')[0] }}
                  </el-menu-item>
                </template>
              </el-menu-item-group>
            </el-submenu>
            <el-menu-item :index="item.path" v-else-if="!item.name.includes('hidden')">
              <template #title>
                <!-- <el-icon>
                    <i :class="`iconfont ${icons[item.name?.split('?')[0]]}`"></i>
                  </el-icon> -->
                {{ item.name?.split('?')[0] }}
              </template>
            </el-menu-item>
          </template>
        </el-menu>
      </div>
      <div class="right">
        <router-view class="content"></router-view>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapse: false,
      show: false,
    }
  },
  mounted() {
    console.log(this.$router.options.routes);
  }
}
</script>
<style lang="scss" scoped>
.Layout {
  width: 100%;
  height: 100%;
  overflow: hidden;

  // background-color: white;
  .header {
    // z-index: 11;
    // position: sticky;
    // top: 0;
    width: 100%;
    height: 60px;
    @include flex-init(space-between);
    padding: 0 32px;
    box-sizing: border-box;
    background-color: #409EFF;

    .logo-container {
      @include grow-shrink(0, 0);
      height: 100%;
      @include flex-init();
      gap: 20px;

      .logo {
        font-weight: bold;
        color: #fff;
        box-sizing: border-box;
        background-image: url('./../../assets/img/logo.png');
        border-radius: 50%;
        @include bg-image(44px, 45px, 100% 100%);
      }

      .title {
        font-size: 24px;
        color: #ffffff;
        font-weight: bold;
        ;
      }
    }


  }

  >.content {
    width: 100%;
    // min-height: calc(100vh - 60px);
    @include flex-init(flex-start, flex-start);
    height: calc(100% - 60px);

    .left {
      width: 260px;
      height: 100%;
      @include grow-shrink(0, 0);
      background-color: #eef1f5;
      overflow: overlay;

      :deep(.el-menu) {
        --el-menu-hover-bg-color: #dde6ee;
        --el-menu-bg-color: #eef1f5;
        --el-menu-item-height: 48px;
        --el-menu-sub-item-height: calc(var(--el-menu-item-height) - 8px);
        border-style: none;

        .el-menu-item-group__title {
          display: none
        }

        // .el-menu-item.is-active{
        //   background-color: #dde6ee;
        // }
        >.el-menu-item {
          font-size: 16px;
        }

        >.el-sub-menu .el-sub-menu__title {
          font-size: 16px;
        }
      }

    }

    .right {
      @include grow-shrink(1, 1);
      box-sizing: border-box;
      height: 100%;
      @include flex-init(flex-start, flex-start, column);
      overflow: hidden;

      >.content {
        @include grow-shrink(1, 1);
        // background-color: white;
        width: 100%;
        overflow: overlay;
      }
    }
  }
}
</style>
