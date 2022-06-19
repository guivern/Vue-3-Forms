<template>
  <div>
    <h1>Create an event</h1>
    <form @submit.prevent="sendForm">

      <fieldset>
        <base-select v-model="event.category" :options="categories" label="Select a category"></base-select>
      </fieldset>

      <fieldset>
        <legend>Name & describe your event</legend>
        <base-input v-model="event.title" label="Title" type="text"></base-input>
        <base-input v-model="event.description" label="Description" type="text"></base-input>
      </fieldset>

      <fieldset>
        <legend>Where is your event?</legend>
        <base-input v-model="event.location" label="Location" type="text"></base-input>
      </fieldset>

      <fieldset>
        <legend>Are pets allowed?</legend>
        <base-radio-group v-model="event.pets" :options="petOptions" name="pets" vertical></base-radio-group>
      </fieldset>

      <fieldset>
        <legend>Extras</legend>
        <div>
          <base-checkbox v-model="event.extras.catering" label="Catering"></base-checkbox>
        </div>
        <div>
          <base-checkbox v-model="event.extras.music" label="Live music"></base-checkbox>
        </div>
      </fieldset>

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
    <pre>
      {{JSON.stringify(event, null, '\t')}}
    </pre>
  </div>
</template>

<script>
import BaseInput from '../components/BaseInput.vue'
import axios from 'axios'

export default {
  components: { BaseInput },
  data () {
    return {
      categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community'
      ],
      event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: true,
        extras: {
          catering: false,
          music: false
        }
      },
      petOptions: [
        { label: 'Yes', value: true },
        { label: 'No', value: false }
      ]
    }
  },
  methods: {
    sendForm () {
      axios.post('https://my-json-server.typicode.com/Code-Pop/Vue-3-Forms/events', this.event)
        .then((response) => { console.log(response.data) })
        .catch((error) => { console.log(error) })
    }
  }
}
</script>
<style scoped>
  fieldset{
    border: 0;
    margin: 0;
    padding: 0;
  }

  legend {
    font-size: 28px;
    font-weight: 700;
    margin-top: 20px;
  }
</style>
