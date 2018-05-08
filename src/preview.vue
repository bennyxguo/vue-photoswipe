<template>
  <div :class="(container == 'background') ? 'photo-swipe-max-size' : ''">
    <div class="my-gallery" itemscope itemtype="http://schema.org/ImageGallery">
      <template v-for="(item, key) in slides">
        <figure
          itemprop="associatedMedia"
          itemscope
          itemtype="http://schema.org/ImageObject"
          :key="key"
          >
          <a :href="item.src" itemprop="contentUrl" :data-id="'preview'+key">
            <img :src="item.msrc" :alt="item.alt" itemprop="thumbnail" v-if="container == 'img'"/>
            <div v-if="container == 'background'" class="photoswipe-container" :style="'background-size:'+bgtype+';background-image:url('+item.src+');'" :data-src="item.src"></div>
            <img :src="item.src" :id="'preview'+key" v-show="false"/>
          </a>
          <figcaption style="display: none" itemprop="caption description">{{item.title}}</figcaption>
        </figure>
      </template>
    </div>
    <div class="pswp" tabindex="-1" role="dialog" aria-hidden="true">
      <div class="pswp__bg"></div>
      <div class="pswp__scroll-wrap">
        <div class="pswp__container">
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
          <div class="pswp__item"></div>
        </div>
        <div class="pswp__ui pswp__ui--hidden">

          <div class="pswp__top-bar">
            <div class="pswp__counter"></div>
            <button class="pswp__button pswp__button--close" title="Close (Esc)"></button>
            <button class="pswp__button pswp__button--share" title="Share"></button>
            <button class="pswp__button pswp__button--fs" title="Toggle fullscreen"></button>
            <button class="pswp__button pswp__button--zoom" title="Zoom in/out"></button>
            <div class="pswp__preloader">
              <div class="pswp__preloader__icn">
                <div class="pswp__preloader__cut">
                  <div class="pswp__preloader__donut"></div>
                </div>
              </div>
            </div>
          </div>
          <div class="pswp__share-modal pswp__share-modal--hidden pswp__single-tap">
            <div class="pswp__share-tooltip"></div>
          </div>
          <button class="pswp__button pswp__button--arrow--left" title="Previous (arrow left)">
          </button>
          <button class="pswp__button pswp__button--arrow--right" title="Next (arrow right)">
          </button>
          <div class="pswp__caption">
            <div class="pswp__caption__center"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
  @import "~photoswipe/dist/photoswipe.css";
  @import "~photoswipe/dist/default-skin/default-skin.css";
  .photoswipe-container {
    width: 100%;
    height: 100%;
    background-repeat: no-repeat;
    background-position: center;
  }

  .photo-swipe-max-size,
  .photo-swipe-max-size figure,
  .photo-swipe-max-size a,
  .photo-swipe-max-size .my-gallery {
    width: 100%;
    height: 100%;
    display:block;
    margin: 0;
    padding: 0;
  }
</style>
