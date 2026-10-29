<script setup lang="ts">
type ButtonProps = {
  variant?: 'primary' | 'secondary' | 'outline' | 'danger'
  size?: 'sm' | 'md' | 'lg'
  disabled?: boolean
  type?: 'button' | 'submit' | 'reset'
}

const {
  variant = 'primary',
  size = 'md',
  disabled = false,
  type = 'button',
} = defineProps<ButtonProps>()
</script>
<template>
  <button :type="type" :disabled="disabled" class="ui-button" :class="[variant, size]">
    <slot />
  </button>
</template>
<style scoped>
.ui-button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: 1px solid transparent;
  border-radius: 4px;
  font-family: inherit;
  font-weight: 500;
  transition:
    background-color 0.2s ease-in-out,
    border-color 0.2s ease-in-out,
    color 0.2s ease-in-out;
  white-space: nowrap;
  user-select: none;
  &:disabled {
    cursor: not-allowed;
    opacity: 0.65;
  }
}

/* variants: primary, secondary, outline, danger */
.ui-button.primary {
  background-color: #007bff;
  color: #fff;
  &:hover {
    background-color: #0056b3;
    border-color: #0056b3;
    color: #fff;
  }
  &:focus-visible {
    outline: 2px solid #0056b3;
    outline-offset: 2px;
  }
  &:active {
    background-color: #004085;
    border-color: #004085;
    color: #fff;
  }
}

.ui-button.secondary {
  background-color: #6c757d;
  color: #fff;
  &:hover {
    background-color: #5a6268;
    border-color: #5a6268;
    color: #fff;
  }
  &:focus-visible {
    outline: 2px solid #5a6268;
    outline-offset: 2px;
  }
  &:active {
    background-color: #545b62;
    border-color: #545b62;
    color: #fff;
  }
}

.ui-button.outline {
  background-color: transparent;
  color: #007bff;
  border-color: #007bff;
  &:hover {
    background-color: #007bff;
    color: #fff;
  }
  &:focus-visible {
    outline: 2px solid #007bff;
    outline-offset: 2px;
  }
  &:active {
    background-color: #0056b3;
    border-color: #0056b3;
    color: #fff;
  }
}

.ui-button.danger {
  background-color: #dc3545;
  color: #fff;
  &:hover {
    background-color: #c82333;
    border-color: #c82333;
    color: #fff;
  }
  &:focus-visible {
    outline: 2px solid #c82333;
    outline-offset: 2px;
  }
  &:active {
    background-color: #bd2130;
    border-color: #bd2130;
    color: #fff;
  }
}
</style>
