<template lang="pug">

// TODO: THEN/ElSE grouping card.group contains then, else to specify it's target

div.margin
  div.card(v-if="!card.broken")
    div(v-for="group in cards" :key="group.id")
      div(v-for="cardInstance in group.cards.action" v-if="cardInstance.id === card.id && group.uri === card.uri")
        flowcard(:card="card" :cardInstance="cardInstance")

  div.card.broken(v-else)
    i.fas.fa-unlink {{card.uriObj}}

</template>

<script>
import flowcard from '@/components/flow/flowcard';

export default {
  name: 'actioncard',
  props: ['cards', 'card'],
  components: {
    flowcard
  }
};

</script>

<style lang="stylus">
@import '~styles/variables.styl'

.margin
  margin 2px
.broken
  text-align center
.card
  font-size 16px
  border-style solid
  border-width 2px
  border-color color-primary
  border-radius 5px
  padding 5px
  width 80%
  margin auto

</style>
