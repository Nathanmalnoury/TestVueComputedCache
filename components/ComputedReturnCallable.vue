<!-- Please remove this file from your project -->
<template>
  <div style="display: flex; flex-direction: column">
    <div>
      <span>    VAR: <strong>{{ variable }}</strong></span>
      <button @click="variable += 1">
        Increase var
      </button>
      <button @click="variable -= 1">
        Decrease var
      </button>
    </div>
    <button @click="toggleDisplay">
      Show computed
    </button>
    <div v-if="showVar">
      <span>Double: {{ double(variable) }}</span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'

@Component
export default class Template extends Vue {
  variable !: number;
  showVar!: boolean;

  data () {
    return {
      variable: 1,
      showVar: false
    }
  }

  toggleDisplay () {
    this.showVar = !this.showVar
  }

  get double () {
    console.log('double getter')
    return (num: number) => {
      console.log('inner function of getter')
      return num * 2
    }
  }
}
</script>
