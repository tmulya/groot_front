<template>
  <div>
    <section id="hero" class="d-flex align-items-center" v-if="page.header_image !== false" :style="{ backgroundImage: `url(${page.header})` }">
      <div class="container">
        <h1>{{ page.headline }}</h1>
        <h2>{{ page.subheadline }}</h2>
        <div class="d-flex" v-if="page.headline_cta">
          <a :href="page.headline_cta_url" class="btn-get-started scrollto">{{ page.headline_cta }}</a>
        </div>
      </div>
    </section>
    <section id="hero2" class="d-flex align-items-center" v-else :style="{ backgroundImage: `url(${page.header})` }">
      <div class="container">
        <h1>{{ page.headline }}</h1>
        <h2>{{ page.subheadline }}</h2>
        <div class="d-flex" v-if="page.headline_cta">
          <a :href="page.headline_cta_url" class="btn-get-started scrollto">{{ page.headline_cta }}</a>
        </div>
      </div>
    </section>
    <div v-html="page.description"></div>
    <section id="gallery" v-if="page.gallery_enable" class="section-bg-white">
      <div class="container">
        <div class="section-title">
          <h2>{{ page.gallery_title }}</h2>
          <h3>{{ page.gallery_subtitle }}</h3>
        </div>
        <vue-masonry-wall :items="page.gallery" :options="{width: 300, padding: 12}" :ssr="{columns: 2}">
          <template v-slot:default="{item}">
            <div class="item-gallery">
              <img :src="item.url" class="img-gallery"/>
              <div class="content-gallery">
                <h5 class="text-ellipsis-1l">{{item.caption}}</h5>
              </div>
            </div>
          </template>
        </vue-masonry-wall>
      </div>
    </section>
    <!-- <pre>{{ page }}</pre> -->
  </div>
</template>

<script>
import axios from 'axios'
import { domainApi } from '@/config'
import VueMasonryWall from "vue-masonry-wall"

export default {
  data() {
    return {
      page: {},
      options: {
        width: 300,
        padding: {
          2: 8,
          default: 12
        }
      }
    }
  },
  components: { VueMasonryWall },
  computed: {
    domain: function () {
      return domainApi
    }
  },  
  async fetch() {
    var param = this.$route.fullPath
    console.log(param)
    if (param === '/') {
      try {
        const response = await axios.get(domainApi + '/pages/home-page')
        const data = response.data
        var gallery = []
        if (data.gallery_enable === true) {
          for (let i = 0; i < data.gallery.length; i++) {
            var obj = {
              url: domainApi + data.gallery[i].url,
              caption: data.gallery[i].caption
            }
            gallery.push(obj)
          }
        }
        this.page = {
          id: data.id,
          description: data.description,
          title: response.data.title,
          published_at: data.published_at,
          created_at: data.created_at,
          updated_at: data.updated_at,
          slug: data.slug,
          preventIndexing: data.preventIndexing,
          keywords: data.keywords,
          header_image: data.header_image,
          headline: data.headline,
          subheadline: data.subheadline,
          headline_cta: data.headline_cta,
          headline_cta_url: data.headline_cta_url,
          seo: {
            id: data.seo.id,
            metaTitle: data.seo.metaTitle,
            metaDescription: data.seo.metaDescription,
            alt: data.alt
          },
          header: domainApi + data.header.url,
          gallery_enable: data.gallery_enable,
          gallery: gallery,
          gallery_title: data.gallery_title,
          gallery_subtitle: data.gallery_subtitle
        }
      } catch (error) {
        console.log(error)
      }
    } else {
      try {
        console.log(domainApi + '/pages' + param)
        const response = await axios.get(domainApi + '/pages' + param)
        const data = response.data
        var gallery = []
        if (data.gallery_enable === true) {
          for (let i = 0; i < data.gallery.length; i++) {
            var obj = {
              url: domainApi + data.gallery[i].url,
              caption: data.gallery[i].caption
            }
            gallery.push(obj)
          }
        }
        this.page = {
          id: data.id,
          description: data.description,
          title: response.data.title,
          published_at: data.published_at,
          created_at: data.created_at,
          updated_at: data.updated_at,
          slug: data.slug,
          preventIndexing: data.preventIndexing,
          keywords: data.keywords,
          header_image: data.header_image,
          headline: data.headline,
          subheadline: data.subheadline,
          headline_cta: data.headline_cta,
          headline_cta_url: data.headline_cta_url,
          seo: data.seo,
          header: data.header ? domainApi + data.header.url : null,
          gallery_enable: data.gallery_enable,
          gallery: gallery,
          gallery_title: data.gallery_title,
          gallery_subtitle: data.gallery_subtitle
        }
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>

<style>
.item-gallery {
  overflow: hidden;
  border-radius: 4px;
  width: 100%;
  background: #F5F5F5;
}
.content-gallery {
  padding: 20px;
}
.img-gallery {
  object-fit: cover;
  width: 100%;
  height: 100%;
  line-height: 0;
  display: block;
}
/*--------------------------------------------------------------
# Hero Section
--------------------------------------------------------------*/
#hero {
  width: 100%;
  height: 640px;
  /* background: url('~/assets/img/header-bg.jpg'); */
  background: #101B40;
  background-attachment: fixed;
  background-position: 50% 50%;
  background-size: cover;
  position: relative;
}
/* #hero::after {
  content: '';
  display: block;
  width: 100%;
  height: 100%;
  background-image: linear-gradient(to top,rgba(21,0,167,0.4),rgba(3,0,42, 0.4));
  position: absolute;
  bottom: 0;
} */

/* #hero:before {
  content: "";
  background: rgba(255, 255, 255, 0.6);
  position: absolute;
  bottom: 0;
  top: 0;
  left: 0;
  right: 0;
} */

#hero .container {
  position: relative;
  padding-top: 132px;
}

@media (max-width: 992px) {
  #hero .container {
    padding-top: 58px;
  }
}

#hero h1 {
  margin: 0;
  font-size: 48px;
  font-weight: 700;
  line-height: 56px;
  color: #F7F8FB;
}

#hero h1 span {
  color: #FE7847;
}

#hero h2 {
  color: #F7F8FB;
  margin: 5px 0 30px 0;
  font-size: 24px;
  font-weight: 400;
}

#hero .btn-get-started {
  text-transform: uppercase;
  font-weight: bold;
  font-size: 14px;
  letter-spacing: 1px;
  display: inline-block;
  padding: 10px 28px;
  border-radius: 4px;
  transition: 0.5s;
  color: #101B40;
  background: #FFC4B2;
}

#hero .btn-get-started:hover {
  background: #FE7847;
}

#hero .btn-watch-video {
  font-size: 16px;
  display: inline-block;
  padding: 10px 25px 8px 40px;
  transition: 0.5s;
  margin-left: 25px;
  color: #222222;
  position: relative;
  font-weight: 600;
}

#hero .btn-watch-video i {
  color: #FE7847;
  font-size: 32px;
  position: absolute;
  left: 0;
  top: 7px;
  transition: 0.3s;
}

#hero .btn-watch-video:hover {
  color: #FE7847;
}

#hero .btn-watch-video:hover i {
  color: #3b8af2;
}
  
@media (min-width: 1024px) {
  #hero {
    background-attachment: fixed;
  }
}
  
@media (max-width: 768px) {
  #hero {
    height: 100vh;
  }
  #hero h1 {
    font-size: 28px;
    line-height: 36px;
  }
  #hero h2 {
    font-size: 18px;
    line-height: 24px;
    margin-bottom: 30px;
  }
  #hero .btn-get-started, #hero .btn-watch-video {
    font-size: 13px;
  }
}
  
@media (max-height: 500px) {
  #hero {
    height: 120vh;
  }
}
/* End Hero */
#hero2 {
  width: 100%;
  height: auto;
  min-height: 440px;
  background: #101B40;
  background-attachment: fixed;
  background-position: 50% 50%;
  background-size: cover;
  /* background-repeat: no-repeat; */
  position: relative;
}

#hero2 .container {
  position: relative;
  padding-top: 132px;
}

@media (max-width: 992px) {
  #hero2 .container {
    padding-top: 58px;
  }
}

#hero2 h1 {
  margin: 0;
  font-size: 48px;
  font-weight: 700;
  line-height: 56px;
  color: #F7F8FB;
}

#hero2 h1 span {
  color: #FE7847;
}

#hero2 h2 {
  color: #F7F8FB;
  margin: 5px 0 30px 0;
  font-size: 24px;
  font-weight: 400;
}

#hero2 .btn-get-started {
  text-transform: uppercase;
  font-weight: bold;
  font-size: 14px;
  letter-spacing: 1px;
  display: inline-block;
  padding: 10px 28px;
  border-radius: 4px;
  transition: 0.5s;
  color: #101B40;
  background: #FFC4B2;
}

#hero2 .btn-get-started:hover {
  background: #FE7847;
}

#hero2 .btn-watch-video {
  font-size: 16px;
  display: inline-block;
  padding: 10px 25px 8px 40px;
  transition: 0.5s;
  margin-left: 25px;
  color: #222222;
  position: relative;
  font-weight: 600;
}

#hero2 .btn-watch-video i {
  color: #FE7847;
  font-size: 32px;
  position: absolute;
  left: 0;
  top: 7px;
  transition: 0.3s;
}

#hero2 .btn-watch-video:hover {
  color: #FE7847;
}

#hero2 .btn-watch-video:hover i {
  color: #3b8af2;
}
  
@media (min-width: 1024px) {
  #hero2 {
    background-attachment: fixed;
  }
}
  
@media (max-width: 768px) {
  #hero2 {
    height: 100vh;
  }
  #hero2 h1 {
    font-size: 28px;
    line-height: 36px;
  }
  #hero2 h2 {
    font-size: 18px;
    line-height: 24px;
    margin-bottom: 30px;
  }
  #hero2 .btn-get-started, #hero2 .btn-watch-video {
    font-size: 13px;
  }
}
  
@media (max-height: 500px) {
  #hero2 {
    height: 120vh;
  }
}
</style>
