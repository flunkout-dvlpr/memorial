<template>
  <q-page>
    <div class="q-pa-md fit row  justify-center  content-center">
      <q-btn outline class="q-mx-sm" color="primary" label="Add Memory" @click="addMemory = true" />
      <q-btn outline class="q-mx-sm" color="primary" label="Add Image" @click="addImage = true" />
    </div>
    <div class="q-pa-md fit row  justify-center  content-center">
      <q-dialog
        v-model="addMemory"
        persistent
      >
        <q-card style="width: 300px">
          <q-card-section>
            <div class="text-h6">Add Memory</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            <q-input outlined v-model="newMemory.title" label="Title" />
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-input outlined v-model="newMemory.author" label="Author" />
          </q-card-section>
          <q-card-section class="q-pt-none">
            <q-input
              outlined
              bottom-slots
              v-model="newMemory.message"
              label="Message"
              type="textarea"
              counter
              maxlength="300"
              :dense="dense"
            >
              <template v-slot:hint>
                Text limit
              </template>
            </q-input>
          </q-card-section>

          <q-card-actions align="right" class="bg-white text-primary">
            <q-btn flat label="Cancel" @click="resetNewMemory()" />
            <q-btn flat label="Add" @click="submitMemory()" />
          </q-card-actions>
        </q-card>
      </q-dialog>

      <q-dialog
        v-model="addImage"
        persistent
      >
        <q-card style="width: 300px">
          <q-card-section>
            <div class="text-h6">Add Image</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            <q-file
              style="max-width: 300px"
              v-model="filesImages"
              filled
              outlined
              label="Select Image"
              multiple
              accept=".jpg, image/*"
              @rejected="onRejected"
            />
          </q-card-section>

          <q-uploader
            style="max-width: 300px"
            url="http://localhost:4444/upload"
            label="Select Image"
            multiple
            accept=".jpg, image/*"
            @rejected="onRejected"
          />

          <q-card-actions align="right" class="bg-white text-primary">
            <q-btn flat label="Cancel" @click="resetNewImage()" />
            <q-btn flat label="Add" @click="submitImage()" />
          </q-card-actions>
        </q-card>
      </q-dialog>

    </div>

    <div class="card-container row q-gutter-sm items-stretch flex-center">
        <q-card
          dark
          bordered
          class="bg-primary card"
          v-for="memory in memories"
          :key="memory.id"
        >
          <q-card-section>
            <div class="text-h6 text-accent">{{memory.title}}</div>
            <div class="text-subtitle2 text-accent">by {{memory.author}}</div>
          </q-card-section>

          <q-separator dark inset />

          <q-card-section class="text-h6">
            {{ memory.message }}
          </q-card-section>
        </q-card>
    </div>
  </q-page>
</template>

<script>
export default {
  name: 'Cards',
  data () {
    return {
      addMemory: false,
      addImage: false,
      filesImages: null,
      newMemory: {
        title: '',
        author: '',
        message: ''
      },
      memories: []
    }
  },
  methods: {
    resetNewMemory () {
      this.addMemory = false
      this.newMemory = {
        title: '',
        author: '',
        message: ''
      }
    },
    resetNewImage () {
      this.addImage = false
      this.filesImages = null
    },
    submitMemory () {
      this.addMemory = false
      this.memories.push(this.newMemory)
      this.newMemory = {
        title: '',
        author: '',
        message: ''
      }
      this.filesImages = null
    },
    submitImage () {
      this.addImage = false
      console.log(this.filesImages)
      this.filesImages = null
    }
  }
}
</script>

<style lang="scss" scoped>
.card-container {
  max-width: 100%;
}
.card {
  width: 20rem;
}
</style>
