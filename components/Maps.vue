<template>
  <section style="overfloe: hidden">
    <GMap
      ref="gMap"
      language="en"
      :cluster="{ options: { styles: clusterStyle } }"
      :center="{ lat: locations[a].lat, lng: locations[a].lng }"
      :options="{ fullscreenControl: false, styles: mapStyle }"
      :zoom="10"
    >
      <GMapMarker
        v-for="location in locations"
        :key="location.id"
        :position="{ lat: location.lat, lng: location.lng }"
        :options="{
          icon: location === currentLocation ? pins.selected : pins.notSelected,
        }"
        @click="currentLocation = location"
      >
        <GMapInfoWindow :options="{ maxWidth: 200 }">
          <code> lat: {{ location.lat }}, lng: {{ location.lng }} </code>
          <v-card-subtitle style="color: red"> {{ location }} </v-card-subtitle>
        </GMapInfoWindow>
      </GMapMarker>
      <!-- <GMapCircle :options="circleOptions" /> -->
    </GMap>

    <div
      style="
        width: 100%;
        overflow: hidden;
        padding-left: 14px;
        padding-right: 14px;
        padding-top: 16px;
      "
    >
      <VueSlickCarousel :arrows="true" :dots="true" v-bind="settings">
        <v-btn
          outlined
          color="white"
          v-for="(location, index) in locations"
          @click="setCenter(index)"
          :key="index"
          class="btn-content"
        >
          {{ location.name }}
        </v-btn>
      </VueSlickCarousel>
    </div>
  </section>
</template>

<script>
import VueSlickCarousel from "vue-slick-carousel";
import "vue-slick-carousel/dist/vue-slick-carousel.css";
// optional style for arrows & dots
import "vue-slick-carousel/dist/vue-slick-carousel-theme.css";
import DetailCards from "~/components/DetailCards.vue";

export default {
  data() {
    return {
      settings: {
        dots: true,
        // "focusOnSelect": true,
        infinite: false,
        speed: 500,
        slidesToShow: 4,
        slidesToScroll: 4,
        touchThreshold: 5,
      },
      a: 0,
      center: { lat: 4.074513033, lng: 101.5178721 },

      mapStyle: [
        {
          elementType: "geometry",
          stylers: [
            {
              color: "#242f3e",
            },
          ],
        },
        {
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#746855",
            },
          ],
        },
        {
          elementType: "labels.text.stroke",
          stylers: [
            {
              color: "#242f3e",
            },
          ],
        },
        {
          featureType: "administrative.locality",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#d59563",
            },
          ],
        },
        {
          featureType: "poi",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#d59563",
            },
          ],
        },
        {
          featureType: "poi.park",
          elementType: "geometry",
          stylers: [
            {
              color: "#263c3f",
            },
          ],
        },
        {
          featureType: "poi.park",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#6b9a76",
            },
          ],
        },
        {
          featureType: "road",
          elementType: "geometry",
          stylers: [
            {
              color: "#38414e",
            },
          ],
        },
        {
          featureType: "road",
          elementType: "geometry.stroke",
          stylers: [
            {
              color: "#212a37",
            },
          ],
        },
        {
          featureType: "road",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#9ca5b3",
            },
          ],
        },
        {
          featureType: "road.highway",
          elementType: "geometry",
          stylers: [
            {
              color: "#746855",
            },
          ],
        },
        {
          featureType: "road.highway",
          elementType: "geometry.stroke",
          stylers: [
            {
              color: "#1f2835",
            },
          ],
        },
        {
          featureType: "road.highway",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#f3d19c",
            },
          ],
        },
        {
          featureType: "transit",
          elementType: "geometry",
          stylers: [
            {
              color: "#2f3948",
            },
          ],
        },
        {
          featureType: "transit.station",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#d59563",
            },
          ],
        },
        {
          featureType: "water",
          elementType: "geometry",
          stylers: [
            {
              color: "#17263c",
            },
          ],
        },
        {
          featureType: "water",
          elementType: "labels.text.fill",
          stylers: [
            {
              color: "#515c6d",
            },
          ],
        },
        {
          featureType: "water",
          elementType: "labels.text.stroke",
          stylers: [
            {
              color: "#17263c",
            },
          ],
        },
      ],

      currentLocation: {},
      // circleOptions: {
      //   ...
      // },

      locations: [
        { name: "Majlis Bandaraya Shah Alam", lat: 3.0734, lng: 101.5194 },
        {
          name: "Bangunan Darul Ehsan",
          lat: 3.074513033,
          lng: 101.5178721,
        },
        {
          name: "Menara MRCB",
          lat: 3.0736,
          lng: 101.5164,
        },
        {
          name: "Bangunan Umno Selangor",
          lat: 3.0736,
          lng: 101.5221,
        },
        {
          name: "Jabatan Audit Negara Negeri Selangor",
          lat: 3.0739,
          lng: 101.5236,
        },
        {
          name: "Wisma PKNS",
          lat: 3.1536,
          lng: 101.6943,
        },
        {
          name: "Plaza Alam Sentral",
          lat: 3.074,
          lng: 101.5172,
        },
        {
          name: "Plaza Anggerik",
          lat: 3.0648,
          lng: 101.7473,
        },
        {
          name: "SACC Mall",
          lat: 3.0718,
          lng: 101.5183,
        },
        {
          name: "Kompleks PKNS",
          lat: 3.0707,
          lng: 101.5173,
        },
        {
          name: "Avisena Specialist Hospital",
          lat: 3.0718,
          lng: 101.5237,
        },
        {
          name: "Plaza Perangsang",
          lat: 3.0729,
          lng: 101.5182,
        },
        // {
        //   name: "Affin Bank",
        //   lat: "3.0729",
        //   lng: "101.5182",
        // },
        // {
        //   name: "Maybank",
        //   lat: "3.0729",
        //   lng: "101.5182",
        // },
        {
          name: "Shah Alam Convention Centre",
          lat: 3.0699,
          lng: 101.5186,
        },
        {
          name: "Masjid Sultan Salahuddin Abdul Aziz Shah",
          lat: 3.0786,
          lng: 101.5207,
        },
        {
          name: "Mardhiyyah Hotel & Suites",
          lat: 3.0737,
          lng: 101.5227,
        },
      ],
      pins: {
        selected:
          "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACMAAAAwCAMAAACsRTNeAAAACXBIWXMAAAAcAAAAHAAPAbmPAAAAZlBMVEUAAADGISHGISHCIR3GISHGJSXGIR3GIR3GIR2+ISHCISHGISHGIR3GISHGIR3CIR3GJSHGIR3GIR3WMSnqQzXOKSXmPzHSLSXiPDHKJSHGJSHeOS3aNS2+HRmyFRHKKSHiOS3iPzF0SiX0AAAAEnRSTlMAhDzGVB2o6rIKnHRoLeLWaN5BSZ8zAAABdUlEQVR42u39V3KEMAxAAZi2fXcTyd203P+SoQTjyk4O8P5g3kio8U3+TVms1NeM0BQVaIGIQsG5eKaUEyhDNziDqgmNJ4CkLnyAh688oKUhRt08RccKpVLf3ESGppBQW2dKlIZDuVWkaQ68bJl41uHqvjgFc9+2iF6ganEqpzGi6yfEHljCrNSwK/3GXqeYSyuUfWbW6fZkp9mx+dt+x3YDO88RjmMDtZB1+v84uDjiMBeeZ8dOwjiOLX6py+nPEIehbO7P9Txuz7zbFBtGwrL+ThMpLoozQHwn5s5H70kX63JUTqAAUf1dWpNZ1XkP7bLeh5+0w052n8mFpTOBc9PNGROKAe+gy+/4NKSqiUcJY6iwCwm46eA6WPxTCL/bdsbD+24DTUIh5WuX3Ev3qPfBsRvJcBn+FHzlFHKFNVsL96xDinUn3THFLLXJrjxyHoofffDK/EvL1b1xwvUyjyiA6/cHZ/qXf0o19RHg+skpi6/w1S8tW0/UXw6dAwAAAABJRU5ErkJggg==",

        notSelected:
          "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACMAAAAwCAMAAACsRTNeAAAACXBIWXMAAAAcAAAAHAAPAbmPAAAAZlBMVEUAAADGISHGISHCIR3GISHGJSXGIR3GIR3GIR2+ISHCISHGISHGIR3GISHGIR3CIR3GJSHGIR3GIR3WMSnqQzXOKSXmPzHSLSXiPDHKJSHGJSHeOS3aNS2+HRmyFRHKKSHiOS3iPzF0SiX0AAAAEnRSTlMAhDzGVB2o6rIKnHRoLeLWaN5BSZ8zAAABdUlEQVR42u39V3KEMAxAAZi2fXcTyd203P+SoQTjyk4O8P5g3kio8U3+TVms1NeM0BQVaIGIQsG5eKaUEyhDNziDqgmNJ4CkLnyAh688oKUhRt08RccKpVLf3ESGppBQW2dKlIZDuVWkaQ68bJl41uHqvjgFc9+2iF6ganEqpzGi6yfEHljCrNSwK/3GXqeYSyuUfWbW6fZkp9mx+dt+x3YDO88RjmMDtZB1+v84uDjiMBeeZ8dOwjiOLX6py+nPEIehbO7P9Txuz7zbFBtGwrL+ThMpLoozQHwn5s5H70kX63JUTqAAUf1dWpNZ1XkP7bLeh5+0w052n8mFpTOBc9PNGROKAe+gy+/4NKSqiUcJY6iwCwm46eA6WPxTCL/bdsbD+24DTUIh5WuX3Ev3qPfBsRvJcBn+FHzlFHKFNVsL96xDinUn3THFLLXJrjxyHoofffDK/EvL1b1xwvUyjyiA6/cHZ/qXf0o19RHg+skpi6/w1S8tW0/UXw6dAwAAAABJRU5ErkJggg==",
      },
      // mapStyle: [...],
      clusterStyle: [
        {
          url: "https://developers.google.com/maps/documentation/javascript/examples/markerclusterer/m1.png",
          width: 56,
          height: 56,
          textColor: "#fff",
        },
      ],
    };
  },
  methods: {
    setCenter: function (index) {
      this.a = index;
      this.$refs.gMap.map.setCenter({
        lat: this.locations[this.a].lat,
        lng: this.locations[this.a].lng,
      });
      this.center = { lat: 41.9028, lng: 12.4964 };
      // map.setCenter();
    },
  },
  components: { VueSlickCarousel, DetailCards },
};
</script>

<style scoped>
.GMap__Wrapper {
  height: 90vh !important;
}

.v-btn {
  white-space: normal;
  padding: 10px;
}

.btn-content {
  font-size: 0.6rem !important;
}
</style>
