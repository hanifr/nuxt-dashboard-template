<template>
  <section id="home" class="jumbotron">
    <div class="jumbotron-center">
    <v-row dense>
      <v-col cols="12" md="3">
        <v-card flat style="background-color: transparent;" outlined>
        <v-toolbar dense color="transparent" rounded>
            <v-toolbar-text>
               Total Energy kWh
              </v-toolbar-text>
          </v-toolbar>
          <v-divider></v-divider>
          <!-- <v-card-text>
            <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit</span>
          </v-card-text> -->
          <v-card-text>
                <TheBandwidthUsage></TheBandwidthUsage>
            </v-card-text>
            <v-card-text>
                <TheBandwidthUsage></TheBandwidthUsage>
            </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card flat style="background-color: transparent;" outlined>
        <v-toolbar dense color="transparent" rounded>
            <v-toolbar-title>Summary of Energy Consumption</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
                <TheSalesOverview></TheSalesOverview>
            </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="3">
        <v-card flat style="background-color: transparent;" outlined>
        <v-toolbar dense color="transparent" rounded>
            <v-toolbar-text>Monthly Building Energy Usage kWh</v-toolbar-text>
          </v-toolbar>
        </v-card>
      </v-col>
    </v-row>
      <!-- <v-sheet outlined color="blue" rounded> -->
    <v-btn depressed outlined class="fb-btn grey--text"> Sign with Facebook </v-btn>
<!-- </v-sheet> -->

    </div>
  </section>
</template>

<script>
import TheBandwidthUsage from '@/components/bandwidth-usage/TheBandwidthUsage'
import TheSalesOverview from '@/components/sales-overview2/TheSalesOverview2'
export default {
  name: "StarterPage",
  components: {
    TheBandwidthUsage: TheBandwidthUsage,
    TheSalesOverview: TheSalesOverview
    // About: About,
    // OurTeam: OurTeam,
    // Features: Features,
    // Subscribe: Subscribe
  },
  data: () => ({
    page: {
      title: "StarterPage"
    },
    elementVisible: false,
    breadcrumbs: [
      {
        text: "StarterPage",
        disabled: true
      }
    ]
  })
};
</script>
