<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: selected && !open }">
      <Gift v-if="open && hasGift" />
    </div>
    <div class="door" :class="{ open }" @click="selected = !selected">
      <div class="number" :class="{ selected }">{{ number }}</div>
      <div class="knob" :class="{ selected }" @click.stop="open = true" title="Click to open the door"></div>
    </div>
  </div>
</template>

<script>
import Gift from './Gift'

export default {
  name: 'Door',
  components: {
    Gift
  },
  props: {
    number: {
      type: String,
      required: true
    },
    hasGift: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      open: false,
      selected: false
    }
  }
}
</script>

<style>
:root {
  --selected-color: yellow;
  --selected-border: 5px solid var(--selected-color);
  --door-border: 5px solid brown;
}

.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #AAA;
  margin-bottom: 20px;
  font-size: 3rem;
  display: flex;
  justify-content: center;
}

.door-frame {
  position: absolute;
  height: 300px;
  width: 180px;
  border-left: var(--door-border);
  border-top: var(--door-border);
  border-right: var(--door-border);
  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.door {
  background-color: chocolate;
  display: flex;
  flex-direction: column;
  padding: 15px;
  text-align: center;
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
}

.door .knob {
  background-color: brown;
  border-radius: 10px;
  cursor: pointer;
  align-self: flex-start;
  margin-top: 60px;
  height: 20px;
  width: 20px;
}

.door-frame.selected {
  border-left: var(--selected-border);
  border-top: var(--selected-border);
  border-right: var(--selected-border);
}

.door .number.selected {
  color: var(--selected-color);
}

.door .knob.selected {
  background-color: var(--selected-color);
}

.door.open {
  background-color: #0007;
}

.door.open .knob {
  display: none;
}

.door.open .number {
  display: none;
}
</style>