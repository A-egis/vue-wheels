<template>
  <button class="w-button" :class="{[`icon-${iconPosition}`]:true}">
    <w-icon class="icon" v-if="icon" :name="icon"></w-icon>
    <w-icon class="loading" name="loading"></w-icon>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>

<script>
export default {
  // props: ['icon', 'iconPosition']
  props: {
    icon: {},
    iconPosition: {
      type: String,
      default: 'left',
      validator: value => value == 'left' || value == 'right'
    }
  }
}
</script>

<style lang="scss">
@keyframes spin {
  0% {
    transform: rotate(0deg)
  }
  100% {
    transform: rotate(360deg)
  }
}

.w-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  font-size: var(--font-size);
  height: var(--button-height);
  padding: 0 1em;
  border-radius: var(--border-radius);
  border: 1px solid var(--border-color);
  background-color: var(--button-bg);
  vertical-align: middle;

  &:hover {
    border-color: var(--border-color-hover);
  }

  &:active {
    background-color: var(--button-active-bg);
  }

  &:focus {
    outline: none;
  }

  > .icon {
    order: 1;
    margin-right: .3em;
  }

  > .content {
    order: 2;
  }

  &.icon-right {
    > .content {
      order: 1;
    }

    > .icon {
      order: 2;
      margin-right: 0;
      margin-left: .3em;
    }
  }

  .loading {
    animation: spin 2s infinite linear;
  }
}

</style>