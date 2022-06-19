<template>
  <div>
    <h1>Create an event</h1>
    <form>
      <base-select v-model="event.category" :options="categories" label="Select a category"></base-select>

      <h3>Name & describe your event</h3>

      <base-input v-model="event.title" label="Title" type="text"></base-input>

      <base-input v-model="event.description" label="Description" type="text"></base-input>

      <h3>Where is your event?</h3>

      <base-input v-model="event.location" label="Location" type="text"></base-input>

      <h3>Are pets allowed?</h3>
      <div>
        <base-radio v-model="event.pets" :value="true" name="pets" label="Yes"></base-radio>
      </div>

      <div>
        <base-radio v-model="event.pets" :value="false" name="pets" label="No"></base-radio>
      </div>

      <h3>Extras</h3>
      <div>
        <base-checkbox v-model="event.extras.catering" label="Catering"></base-checkbox>
      </div>
      <div>
        <base-checkbox v-model="event.extras.music" label="Live music"></base-checkbox>
      </div>

      <button class="button -fill-gradient" type="submit">Submit</button>
    </form>
    <pre>
      {{JSON.stringify(event, null, '\t')}}
    </pre>
  </div>
</template>

<script>
import BaseInput from '../components/BaseInput.vue'
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
      }
    }
  }
}
</script>
