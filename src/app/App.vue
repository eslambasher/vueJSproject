<template>
    <div class="centered-container">
        <div class="col-sm-12">
            <router-view></router-view>
            <div v-if="alert.message" :class="`alert ${alert.type}`">{{alert.message}}</div>
        </div>
    </div>
</template>

<script>
import { mapState, mapActions } from 'vuex'
import Vue from 'vue'
import VueMaterial from 'vue-material'
import 'vue-material/dist/vue-material.min.css'
import 'vue-material/dist/theme/default.css'

Vue.use(VueMaterial)


export default {
    name: 'app',
    computed: {
        ...mapState({
            alert: state => state.alert
        })
    },
    methods: {
        ...mapActions({
            clearAlert: 'alert/clear' 
        })
    },
    watch: {
        $route (to, from){
            this.clearAlert();
        }
    } 
};
</script>