<template>
  <svg :class="svgClass" aria-hidden="true">
    <use :xlink:href="iconName" />
  </svg>
</template>

<script>
export default {
  name: "Icon",
  props: {
    icon: {
      type: String,
      required: true,
    },
    iconClass: {
      type: String,
    },
  },
  computed: {
    iconName() {
      return `icon${this.icon}`;
    },
    svgClass() {
      if (this.iconClass) {
        return `svg-icon svg-icon-${this.icon} ${this.iconClass}`;
      } else {
        return `svg-icon svg-icon-${this.icon}`;
      }
    },
  },
};
</script>
<style lang="stylus" scoped>
.svg-icon 
  width: 1em;
  height: 1em;
  vertical-align: -0.15em;
  fill: currentColor;
  overflow: hidden;

</style>
