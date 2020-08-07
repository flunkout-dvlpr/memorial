<template>
    <q-footer elevated class="bg-dark q-mt-sm q-pb-sm">
      <div>
        <q-tabs
          v-model="tab"
          inline-label
          align="center"
          class="text-accent desktop-only mobile-hide"
        >
          <q-tab
            name="location"
            icon="ion-pin"
            label="location"
            @click="goToLink('https://goo.gl/maps/FYr2cyzAxfaZ3Jbw9')"
            class="q-mx-md"
          />

          <q-tab
            name="stream"
            icon="ion-videocam"
            label="stream"
            @click="goToLink('https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.oneroomstreaming.com%2Fview%2Fauthorise.php%3Fk%3D159675495071092%26fbclid%3DIwAR2Tj3NR3TsKeqhFvIpot7eclDu4TW2FKetRuyuJVeIrEs_4pEik6AYX_SM&h=AT0yZ0vqsMgwmV0wEs7lsMtspToXsDPNxSS87g0Oqmxp8lpumHGB2T1XOw14TeX0BuvItR7NWvdtGk_6KyuweVmRN6t-0_7KWyR1qtKX-Al8Rg_FJSZdq4ZKxIol9y85Qs_YgmehfA&__tn__=%2CmH-R&c[0]=AT2ZOAsOMTsghP7DwPbur9NT0p9rMJjPolCm83yzjAZOjcrSWh57sOVHJupnhBTBxLeJgcuD-f_HT7AqBwBAtlaLKy2e4u3FnfQcmS96X4l1OD0u86eAwOFGmw4ybDrnPvI9vOSE')"
            class="q-mx-md"
          />

          <q-tab
            name="go fundeme"
            icon="ion-gift"
            label="go fundeme"
            @click="goToLink('https://www.gofundme.com/f/fund-for-jose-solano?utm_source=customer&utm_campaign=p_cp+share-sheet&utm_medium=copy_link_mor')"
            class="q-mx-md"
          />
        </q-tabs>
      </div>

      <q-tabs
        v-model="tab"
        inline-label
        swipeable
        align="center"
        class="column flex flex-center text-accent mobile-only desktop-hide"
      >
        <div class="row justify-between">
          <q-tab
            name="location"
            icon="ion-pin"
            label="location"
            @click="goToLink('https://goo.gl/maps/FYr2cyzAxfaZ3Jbw9')"
            class="q-mx-xs"
          />
          <q-tab
            name="stream"
            icon="ion-videocam"
            label="stream"
            @click="goToLink('https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.oneroomstreaming.com%2Fview%2Fauthorise.php%3Fk%3D159675495071092%26fbclid%3DIwAR2Tj3NR3TsKeqhFvIpot7eclDu4TW2FKetRuyuJVeIrEs_4pEik6AYX_SM&h=AT0yZ0vqsMgwmV0wEs7lsMtspToXsDPNxSS87g0Oqmxp8lpumHGB2T1XOw14TeX0BuvItR7NWvdtGk_6KyuweVmRN6t-0_7KWyR1qtKX-Al8Rg_FJSZdq4ZKxIol9y85Qs_YgmehfA&__tn__=%2CmH-R&c[0]=AT2ZOAsOMTsghP7DwPbur9NT0p9rMJjPolCm83yzjAZOjcrSWh57sOVHJupnhBTBxLeJgcuD-f_HT7AqBwBAtlaLKy2e4u3FnfQcmS96X4l1OD0u86eAwOFGmw4ybDrnPvI9vOSE')"
            class="q-mx-xs"
          />
          <q-tab
            name="go fundeme"
            icon="ion-gift"
            label="go fundeme"
            @click="goToLink('https://www.gofundme.com/f/fund-for-jose-solano?utm_source=customer&utm_campaign=p_cp+share-sheet&utm_medium=copy_link_mor')"
            class="q-mx-xs"
          />
        </div>
      </q-tabs>

      <div class="q-mt-xs">

        <p class="text-center text-h7 text-accent q-mb-none">
          <q-icon name="copyright" />
          Copyright Clean Code LLC.
        </p>
        <div class="text-center text-accent">
          All Rights Reserved
        </div>

      </div>

    </q-footer>
</template>

<script>
export default {
  name: 'Footer',
  data () {
    return {
      tab: ' '
    }
  },
  methods: {
    goToLink (link) {
      window.open(link)
    }
  }
}
</script>

<style lang="scss">

</style>
