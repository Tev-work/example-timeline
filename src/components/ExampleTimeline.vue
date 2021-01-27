<template>
  <div class="example-timeline">
    <h1>Timeline</h1>
    <ol>
      <li
        v-for="entry in sortedCollection"
        :key="entry._id"
      >
        <p class="date">{{ entry.registered }}</p>
        <p>
          <span class="name">{{ entry.name.first }} {{ entry.name.last }}: </span>
          <span class="about">{{ entry.about }}</span>
        </p>
        <p class="tags">Tags: {{ entry.tags.join(', ') }}</p>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'ExampleTimeline',
  props: {
    data: {
      validator(value) {
        if (!Array.isArray(value)) {
          return false;
        }

        return value.reduce((result, entry) => {
          return result && entry && typeof entry === 'object';
        }, true);
      }
    }
  },
  computed: {
    sortedCollection() {
      // TODO date output format has to be modified based on context (e.g. some props enum)

      // TODO maybe use some immutable stuff - depends how much will this data be reused
      const sortedCollection = this.data.slice();
      return sortedCollection.sort((entryA, entryB) => {
        // TODO something nicer, with proper checks - how reliable is our input?
        return new Date(entryA.registered) - new Date(entryB.registered);
      });
    }
  }
}
</script>

<style scoped>
  li {
    list-style-type: none;
    display: block;
    text-align: left;
  }

  .date, .name {
    font-weight: 600;
  }
  .date {
    color: darkcyan;
  }
  .about, .name, .tags {
    font-size: 12px;
  }
</style>
