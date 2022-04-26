<template>
    <v-app-bar fixed height="40" :color="navbar_background" :flat="!navbar_scrolled">
        <v-container class="pa-0 d-flex justify-space-between">
            <v-app-bar-title class="headline text-truncate">
                <NuxtLink to="/" style="text-decoration:none">
                    <h2 id="brand">
                    <img class="mr-1" :src="require('../assets/images/selangor-icon.svg')" height="14"/>
                    SITE INTEGRATION MONITORING SYSTEM (SIMS)    
                    </h2>
                </NuxtLink>
            </v-app-bar-title>
                  <!-- <v-avatar
        :color="$vuetify.breakpoint.smAndDown ? 'grey darken-1' : 'transparent'"
        size="32"
      ></v-avatar> -->
            <nav id="navbar_nav">
                <NuxtLink class="navbar-item" to="/">Home</NuxtLink>
                <a v-for="(item, index) in navbar_items" :key="index" :href="item.href" class="navbar-item">{{item.name}}</a>
            </nav>
        </v-container>
    </v-app-bar>
</template>

<script>
export default {
    name: "Navbar",
    data(){
        return{
            navbar_background: "theme_light",
            navbar_toggle_to_sticky_mode_bk: 20,
            navbar_scrolled: false,
            navbar_items: [
                {
                    name: "Features",
                    href: "#features"
                },
                {
                    name: "Client",
                    href: "#client"
                },
                {
                    name: "Price",
                    href: "#price"
                },
                {
                    name: "Contact",
                    href: "#contact"
                },
            ]
        }
    },
    methods: {
        navbar_check_sticky(){
            let scrollY = window.scrollY;
            if (scrollY >= this.$data.navbar_toggle_to_sticky_mode_bk) {
                this.$set(this.$data, 'navbar_background', "blured")
                this.$set(this.$data, 'navbar_scrolled', true)
                document.querySelector('.v-app-bar')
            }
            else{
                this.$set(this.$data, 'navbar_scrolled', false)
                this.$set(this.$data, 'navbar_background', "theme_color")
            }
        }
    },
    mounted(){
        this.navbar_check_sticky();
        window.onscroll = () => {
            this.navbar_check_sticky();
        }
    }
}
</script>