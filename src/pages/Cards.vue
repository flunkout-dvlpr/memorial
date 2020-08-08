<template>
  <q-page>
    <div class="q-pa-md fit row  justify-center  content-center">
      <q-btn outline class="q-mx-sm" color="primary" label="Share A Memory" @click="addMemory = true" />
      <q-btn outline class="q-mx-sm" color="primary" label="Share An Image" @click="addImage = true" />
    </div>
    <div class="q-pa-md fit row  justify-center  content-center">
      <q-dialog
        v-model="addMemory"
        persistent
      >
        <q-card style="width: 300px">
          <q-form @submit="submitMemory()" @reset="resetNewMemory()" class="q-gutter-md">
            <q-card-section>
              <div class="text-h6">Share Memory</div>
            </q-card-section>

            <q-card-section class="q-pt-none q-pb-none">
              <q-input
                outlined
                v-model="newMemory.first_name"
                label="First Name"
                :rules="[ val => val && val.length > 0 || 'Please enter a first name']"
              />
            </q-card-section>
            <q-card-section class="q-pt-none q-pb-none">
              <q-input
                outlined
                v-model="newMemory.last_name"
                label="Last Name"
                :rules="[ val => val && val.length > 0 || 'Please enter a last name']"
              />
            </q-card-section>
            <q-card-section class="q-pt-none q-pb-none">
              <q-input
                outlined
                v-model="newMemory.email"
                label="Email (Optional)"
              />
            </q-card-section>
            <q-card-section class="q-pt-none q-pb-none">
              <q-input
                outlined
                v-model="newMemory.title"
                label="Title"
                :rules="[ val => val && val.length > 0 || 'Please enter a title']"
              />
            </q-card-section>

            <q-card-section class="q-pt-none q-pb-none">
              <q-input
                outlined
                bottom-slots
                v-model="newMemory.message"
                label="Message"
                type="textarea"
                counter
                maxlength="300"
                :rules="[ val => val && val.length > 0 || 'Please enter a message']"
              >
                <template v-slot:hint>
                  Text limit
                </template>
              </q-input>
            </q-card-section>

            <q-card-actions align="right" class="bg-white text-primary">
              <q-btn flat label="Cancel" v-close-popup type="reset"/>
              <q-btn flat label="Share" type="submit"/>
            </q-card-actions>
          </q-form>
        </q-card>
      </q-dialog>
      <q-dialog
        v-model="addImage"
        persistent
      >
        <q-card style="width: 300px">
          <q-card-section class="q-pa-none">
            <q-uploader
              style="max-width: 300px"
              url="http://localhost:4444/upload"
              label="Share Image"
              accept=".jpg, image/*"
            />
          </q-card-section>
          <q-card-actions align="right" class="bg-white text-primary">
            <q-btn flat label="Cancel" v-close-popup @click="resetNewImage()" />
            <q-btn flat label="Share" @click="submitImage()" />
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
          <div class="text-subtitle2 text-accent">by {{memory.first_name}} {{memory.last_name}}</div>
        </q-card-section>

        <q-separator dark inset />

        <q-card-section class="text-h6">
          <p class="message">{{ memory.message }}</p>
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
        title: null,
        first_name: null,
        last_name: null,
        email: null,
        message: null
      },
      memories: []
    }
  },
  methods: {
    resetNewMemory () {
      this.newMemory = {
        title: null,
        first_name: null,
        last_name: null,
        email: null,
        message: null
      }
    },
    resetNewImage () {
      this.filesImages = null
    },
    submitMemory () {
      this.addMemory = false
      return this.$axios.post('memory/add', this.newMemory).then((response) => {
        if (response.data.type === 'success') {
          this.memories.push(response.data.payload)
          console.log(response.data.payload)
          this.newMemory = {
            title: null,
            first_name: null,
            last_name: null,
            email: null,
            message: null
          }
          this.triggerPositive()
        }
      })
    },
    triggerPositive () {
      this.$q.notify({
        type: 'positive',
        message: 'Memory Submitted, Thank You!'
      })
    },
    submitImage () {
      this.addImage = false
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
.message {
  display:block;
  width:18rem;
  word-wrap:break-word;
}
</style>
