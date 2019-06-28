<template>
    <md-app md-waterfall md-mode="fixed-last">
      <md-app-toolbar class="md-large md-dense md-primary">
        <div class="md-toolbar-row">
          <div class="md-toolbar-section-start">

            <span class="md-title">MyYoutube</span>
          </div>

          <div class="md-toolbar-section-end">
            <md-button to="/login" class="md-primary">Logout</md-button>
          </div>
        </div>

        <div class="md-toolbar-row">
          <md-tabs class="md-primary">
            <md-tab id="tab-home" md-label="All Video" v-on:click="tab = 1">
                
            </md-tab>
            <md-tab id="tab-pages" md-label="Upload file" v-on:click="tab = 2"></md-tab>
            <md-tab id="tab-posts" md-label="Search" v-on:click="tab = 3"></md-tab>
          </md-tabs>
        </div>
      </md-app-toolbar>

      <md-app-content v-if="tab == 1">
          <div class="md-layout">
          <div class="md-layout-item md-size-30">
          <md-list>
            <md-list-item v-bind:key="tag.name" v-for="tag in tags" v-on:click="currentTag = tag">
              <md-icon>move_to_inbox</md-icon>
              <span class="md-list-item-text">{{tag.name}}</span>
            </md-list-item>
          </md-list>
          </div>
          <div class="md-layout-item">
            <md-content v-if="currentTag.name" class="md-elevation-3">
              <span class="md-title">
                Current video : {{currentTag.name}}
              </span>
            </md-content>
            <video v-if="currentTag.video" class="video" width="1000" controls :src="currentTag.video"></video>
            <md-empty-state
              v-else
              md-icon="devices_other"
              md-label="Create your first project"
              md-description="Creating project, you'll be able to upload your design and collaborate with people.">
              <md-button class="md-primary md-raised">Create first project</md-button>
            </md-empty-state>
          </div>
          </div>
      </md-app-content>
      <md-app-content v-if="tab == 2">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error quibusdam, non molestias et! Earum magnam, similique, quo recusandae placeat dicta asperiores modi sint ea repudiandae maxime? Quae non explicabo, neque.</p>
      </md-app-content>
      <md-app-content v-if="tab == 3">
        <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error quibusdam, non molestias et! Earum magnam, similique, quo recusandae placeat dicta asperiores modi sint ea repudiandae maxime? Quae non explicabo, neque.</p>
      </md-app-content>
    </md-app>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import Vue from 'vue'
import Tab from './Tab'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'
import Media from '@dongido/vue-viaudio'

Vue.use(VueMaterial)
export default {
    name: 'Home',
    components: {
      Media
    },
    data: () => ({
        menuVisible: false,
        tab: 1,
        currentTag: {
          video: null,
          name: null
        },
        tags: [
          {
          video: 'http://videohd.jeuxvideo.com/200609/zelda_2_vido_3-00000350-high.mp4',
          name: 'test 1'
          },
            {
            video: 'http://videohd.jeuxvideo.com/200609/zelda_2_vido_3-00000350-high.mp4',
            name: 'test'
          }
        ]
    })
};
</script>

<style>
.md-elevation-3 {
  padding: 16px;
  text-align: center;
  margin: 3%
}
video{
      margin-left: 15%;
}
</style>


