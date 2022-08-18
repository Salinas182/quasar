<template>
  <q-page class="q-ma-md">
    <span class="text-h3">Forms</span>
    <q-separator spaced />

    <div class="row justify-center">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-md col-12 col-md-6 q-pt-xl"
      >
        <q-input
          filled
          v-model="user.name"
          label="Your name *"
          hint="Name and surname"
          lazy-rules
          no-error-icon
          :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input
          filled
          type="number"
          v-model="user.age"
          label="Your age *"
          lazy-rules
          no-error-icon
          :rules="[
            val => val !== null && val !== '' || 'Please type your age',
            val => val > 0 && val < 100 || 'Please type a real age'
          ]"
        />

        <q-toggle 
          v-model="user.conditions"
          label="I accept the license and terms"
          :style="user.errorInConditions && !user.conditions && 'color: red'"
        />

        <div class="row justify-end">
          <q-btn label="Submit" type="submit" color="primary"/>
          <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useQuasar } from 'quasar'

export default defineComponent({
  name: 'FormsPage',
  setup() {
    const $q = useQuasar()
    const user = ref({
      name: '',
      age: '',
      conditions: false,
      errorInConditions: false,
    })

    return {
      user,
      onSubmit() {
        user.value.errorInConditions = false
        if(!user.value.conditions) {
          user.value.errorInConditions = true
          $q.notify({
            message:'Terms and conditions must be accepted.',
            color: 'negative',
            icon: 'las la-exclamation-circle'
          })
          return
        }
        console.log(user.value)
      },
      onReset() {
        user.value = {
          name: '',
          age: '',
          conditions: false,
          errorInConditions: false,
        }
      }
    }
  }
})
</script>
