<template>
  <div>
    <div class="contact-info" id="contact-info">
      <img v-if="!isMobile" class="tree tree1" src="@/projects/tian-hui/house_info/tree1.png" />
      <img v-if="!isMobile" class="tree tree2" src="@/projects/tian-hui/house_info/tree2.png" />
      <butterfly1 v-if="!isMobile" class="butt butt"/>
      <img class="logo" src="@/projects/tian-hui/house_info/logo.png" />
      <div class="info">
        <div class="btn flex-c" @click="showCallDialog">
          <span class="flex-c">
            <font-awesome-icon icon="phone" />
            {{ info.phone }}
          </span>
        </div>
        <div class="btn flex-c" @click="showMessengerDialog">
          <span class="flex-c">
            <font-awesome-icon :icon="['fab', 'facebook-messenger']" /><span
              >FB 諮詢</span
            >
          </span>
        </div>
        <a class="btn flex-c" :href="info.fbLink" target="_blank">
          <span class="flex-c">
            <font-awesome-icon :icon="['fab', 'facebook-f']" /><span
              >前往粉絲專頁</span
            >
          </span>
        </a>
        <div class="address flex-c">{{ info.address }}</div>
        <div class="google-btn flex-c" @click="showMapDialog">
          <span class="flex-c">
            <font-awesome-icon icon="map-marker-alt" /><span
              >導航 Google 地圖</span
            >
          </span>
        </div>
      </div>
    </div>
    <el-dialog
      title
      :visible.sync="isShowCallDialog"
      :width="isMobile ? '90%' : '500px'"
      :modal-append-to-body="false"
    >
      <CallDialog :phone="info.phone" />
    </el-dialog>
    <el-dialog
      title
      :visible.sync="isShowMessengerDialog"
      :width="isMobile ? '90%' : '500px'"
      :modal-append-to-body="false"
    >
      <MessengerDialog :messenger="info.fbMessage" />
    </el-dialog>
    <el-dialog
      title
      :visible.sync="isShowMapDialog"
      :width="isMobile ? '90%' : '500px'"
      :modal-append-to-body="false"
    >
      <MapDialog :link="info.googleLink" :address="info.address" />
    </el-dialog>
  </div>
</template>

<script>
import info from '@/info'
import { isMobile, isTablet } from '@/utils'
import CallDialog from '@/components/Dialog/Call'
import MessengerDialog from '@/components/Dialog/Messenger'
import MapDialog from '@/components/Dialog/Map'
import butterfly1 from '@/projects/tian-hui/butterfly1.vue'
export default {
  name: 'contactInfo',
  components: {
    CallDialog,
    MessengerDialog,
    MapDialog,
    butterfly1
  },
  data() {
    return {
      info,

      isMobile,
      isTablet,
      isShowCallDialog: false,
      isShowMessengerDialog: false,
      isShowMapDialog: false
    }
  },
  methods: {
    showCallDialog() {
      // if (!this.isMobile) return
      this.isShowCallDialog = true
    },
    showMessengerDialog() {
      // if (!this.isMobile) return
      this.isShowMessengerDialog = true
    },

    showMapDialog() {
      // if (!this.isMobile) return
      this.isShowMapDialog = true
    }
  }
}
</script>

<style lang="scss" scoped>
@import "@/assets/style/variableColor.scss";
@import "@/assets/style/variableDefault.scss";
@import "@/projects/tian-hui/sass/share.sass";

.contact-info {
  background: $contact_bg;
  background-size: 100% auto;
  background-position: center bottom;
  //box-shadow: $contact_shadow;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: space-between;
  position: relative;
  z-index: 3;
  width: 100%;
  // height: 480px;
  /* background-size: 100vw auto;
  background-attachment: fixed;
  background-position: 0% 50%; */
  transform: translateY(0);
  margin: 2vw auto 0;
  padding: 70px 0 60px;

  .decor-5 {
    width: 22vw;
    top: -12vh;
    left: -2vw;
    z-index: 5;

    img {
      width: 100%;
    }
  }
}

.logo {
  width: auto;
  height: 145px;
  margin: 0 auto;
  margin-bottom: 60px;
}
.info {
  position: relative;
  z-index: 1;
  width: 880px;
  max-width: 96%;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 20px;
}

.btn {
 // width: 280px;
  flex:1 200px;
  height: 60px;
  font-size: 16px;
  margin-bottom: 20px;
  cursor: pointer;
  text-decoration: none;
  color: #000;
  // box-shadow: $contact_btn_border;
  transition: all 0.5s;
  position: relative;
  overflow: hidden;
  border-radius: 0;
  font-family: $family4;
  cursor: pointer;
  background-color: #fff;
  border: {
    style: solid;
    width: 1px;
    color: #fff!important;
  }
  &:hover {
    background-color: rgba(255,255,255,.5);
  }
  &.half {
    width: 49%;
  }
  svg {
    color: #000;
    width: 24px;
    height: 24px;
    margin-right: 12px;
    transition: all 0.5s;
  }

  &:hover {
    // background: $contact_btn_hover_bg;
    // color: $contact_btn_hover_color;

    svg {
      color: #000;
    }
  }
  &::before {
    content: "";
    width: 40%;
    height: 100%;
    display: block;
    background: #fff;
    position: absolute;
    -webkit-transform: skewX(-20deg);
    transform: skewX(-20deg);
    left: -10%;
    opacity: 0;
    top: 0;
    z-index: 5;
    transition: all 0.4s cubic-bezier(0.2, 0.95, 0.57, 0.99);
  }
  &:hover:before {
    opacity: 1;
    width: 90%;
    left: 140%;
  }
}
.address {
  flex:2 400px;
  height: 60px;
  margin: 0 -20px 0 0;
  background-color: #EDEDED;
  // box-shadow: $contact_btn_border;
  border-radius: 0;
  font-family: $family4;
  color: #000;
  + .google-btn,
  + .btn {
    border-radius: 0;
    font-family: $family4;
  }
}
.google-btn {
  flex:1 200px;
  height: 60px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  text-decoration: none;
  color: #000;
  // background: #d1b373;
  background-position: center !important;
  background-color: #fff;
  // background-image: linear-gradient(180deg, #BDE5FF 0%, #83B9D5 47.92%, #002B43 100%);
  // box-shadow: #d1b373;
  transition: all 0.5s;

  svg {
    color: #000;
    width: 24px;
    height: 24px;
    margin-right: 12px;
    transition: all 0.5s;
  }

  &:hover {
    background: rgba(255,255,255,.5);
    // color: $contact_google_hover_btn_color;

    svg {
      // color: $contact_google_hover_btn_icon;
    }
  }
}

/* 平板尺寸 */
@media only screen and (min-device-width: 768px) and (max-device-width: 1024px) {
  .contact-info {
    display: flex;
    width: 90% !important;
    height: 460px;
    padding: 60px 0 80px;

    .logo {
      width: $contact_logo_tablet_width;
    }
  }
}

/* 手機尺寸 */
@media only screen and (max-width: 767px) {
  .contact-info {
    background-image: none;
    display: flex;
    width: 100%;
    height: auto;
    padding: 20px 30px 30px;
    transform: none;
    position: static;
    // margin: 0 auto 40px auto;

    .logo {
      width: 55vw;
      height: auto;
    }
  }

  .btn {
    width: 100%;
    &.half {
      width: 280px;
    }
    svg {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      left: calc(50% - 6em);
      margin-right: 0;
      + span {
        margin-left: 1.5em;
      }
    }
  }

  .info {
    width: 100%;
    justify-content: center;
    text-align: center;
    gap: 0;
    //margin-bottom: 40px;

    > * {
      // margin-bottom: 26px;
      &.address {
        margin-bottom: 0;
      }
    }
  }

  .logo {
    margin-bottom: 20px;
    margin: 20vw auto 10vw;
    left: auto;
    position: relative;
  }

  .address {
    width: 100%;
    text-align: justify;
    border-radius: 0;
    height: auto;
    line-height: 1.7;
    padding: 1em 1em;
    margin: 0 0 0 0;
    + .google-btn,
    + .btn {
      border-radius: 0;
      width: 100%;
    }
  }
}

@media only screen and (max-width: 321px) {
  .address {
    font-size: 14px;
  }
}
</style>

<style lang="sass">
@import "src/assets/style/myvar"
@media screen and (min-width: $bp-pc)
  .tree
    position: absolute
  .tree1
    width: 25vw
    left: 0
    bottom: 0
  .tree2
    width: 10vw
    right: 0
    top: -8vw

// butterfly
.butt
  position: absolute

@media screen and (min-width: $bp-pc)
  .butt
    right: 9vw
    bottom: 36vw
    width: 4vw
</style>
