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
            @click="goToLink('https://www.oneroomstreaming.com/view/authorise.php?k=159675495071092')"
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
            @click="goToLink('https://www.oneroomstreaming.com/view/authorise.php?k=159675495071092')"
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
