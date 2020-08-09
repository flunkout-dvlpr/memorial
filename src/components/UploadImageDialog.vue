<template>
  <q-dialog ref="dialog" @hide="onDialogHide">
    <q-uploader
      :url="url"
      method="PUT"
      :headers="[{'Content-Type': 'image/png'}]"
      max-files="1"
      color="primary"
      :send-raw="true"
      @finish="hide"
    />
  </q-dialog>
</template>

<script>
export default {
  name: 'UploadImageDialog',
  props: {
    url: {
      type: String,
      required: true
    }
  },
  methods: {
    show () {
      this.$refs.dialog.show()
    },
    hide () {
      this.$refs.dialog.hide()
    },
    onDialogHide () {
      this.$emit('hide')
    }
  }
}
</script>
