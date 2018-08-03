<template>
  <demo-section class="lasy-section">
    <demo-block :title="$t('basicUsage')">
      <div class="lasy-img-container" v-for="(img, index) in imageList" :key="index">
        <img alt="图片" v-lazy="img">
      </div>
    </demo-block>

    <demo-block :title="$t('title2')" class="lasy-img-background">
      <div v-for="(img, index) in backgroundImageList" v-lazy:background-image="img" :key="index" />
    </demo-block>

    <demo-block :title="$t('title3')">
      <lazy-component @show="handleComponentShow">
        <img v-for="(img, index) in componentImageList" v-lazy="img" :key="index" class='lasy-img-component'>
      </lazy-component>
    </demo-block>
  </demo-section>
</template>

<script>
export default {
  i18n: {
    'zh-CN': {
      title2: '背景图懒加载',
      title3: '懒加载模块'
    },
    'en-US': {
      title2: 'Lazyload Background Image',
      title3: 'Lazyload Component'
    }
  },

  data() {
    return {
      imageList: [
        'http://idiy.haier.com/upload/test/76821cf3-459c-48cd-bfb8-1ee9af2178c0.jpg',
        'http://imcommunity.haier.net/group1/M00/00/03/Cp8lIltWuWuAUIH9AAIA059Pv0g975.jpg',
        'http://imcommunity.haier.net/group1/M00/00/08/Cp8l5VtWuaCAezu1AABSp06pXxU162.jpg',
        'https://img.yzcdn.cn/public_files/2017/09/05/c0dab461920687911536621b345a0bc9.jpg'
      ],
      backgroundImageList: [
        'https://img.yzcdn.cn/public_files/2017/09/05/bac1903e863834ace25773f3554b6890.jpg',
        'https://img.yzcdn.cn/public_files/2017/09/05/138c32d4384b5e4a78dc4e1ba58e6a80.jpg'
      ],
      componentImageList: [
        'https://img.yzcdn.cn/public_files/2017/09/05/100a7845756a70af2df513bdd1307d0e.jpg',
        'https://img.yzcdn.cn/public_files/2017/09/05/8a4f5be8289cb3a7434fc19a3de780a2.jpg'
      ]
    };
  },

  methods: {
    handleComponentShow(component) {
      console.log('component show');
      console.log(component);
    }
  }
};
</script>

<style lang="postcss">
.demo-lazyload {
  padding: 0 15px;

  .lasy-img-background.img,
  .lasy-img-component,
  .lasy-img-background div[lazy] {
    padding: 15px;
    width: 100%;
    height: 250px;
    margin: 10px 0 0;
    background-color: white;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
    background-size: 315px 250px;
    background-position: 15px;
    background-repeat: no-repeat;
    box-sizing: border-box;
  }

  .van-doc-demo-block__title,
  .van-doc-demo-section__title {
    padding-left: 0;
  }
}

.lasy-img-container {
  position: relative;
  padding-top: 100%;
  margin-top: 10px;
  height: 0;
  display: block;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
}

.lasy-img-container > img {
  width: auto;
  max-width: 100%;
  max-height: 100%;
  display: block;
  margin: auto;
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
}
</style>
