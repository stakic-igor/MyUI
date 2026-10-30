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
  padding: var(--btn-py) var(--btn-px);
  font-size: var(--btn-fs);
  border-color: var(--btn-border, transparent);
  color: var(--btn-color, #fff);

  &:hover:not(:disabled) {
    background-color: var(--btn-hover);
    border-color: var(--btn-hover);
    color: #fff;
  }
  &:active:not(:disabled) {
    background-color: var(--btn-active);
    border-color: var(--btn-active);
    color: #fff;
  }
  &:focus-visible {
    outline: 2px solid var(--btn-hover);
    outline-offset: 2px;
  }
  &:disabled {
    cursor: not-allowed;
    opacity: 0.65;
  }

  /* variants */
  &.primary {
    background-color: var(--ui-color-primary);
    --btn-hover: var(--ui-matisse-600);
    --btn-active: var(--ui-matisse-700);
  }
  &.secondary {
    background-color: var(--ui-color-secondary);
    --btn-hover: var(--ui-daintree-600);
    --btn-active: var(--ui-daintree-700);
  }
  &.outline {
    background-color: transparent;
    border-color: var(--ui-color-outline);
    color: var(--ui-color-outline);
    --btn-hover: #007bff;
    --btn-active: #0056b3;
  }
  &.danger {
    background-color: var(--ui-color-danger);
    --btn-hover: var(--ui-mint-tulip-400);
    --btn-active: var(--ui-mint-tulip-600);
  }

  /* sizes */
  &.sm {
    min-height: 44px;
    --btn-py: 4px;
    --btn-px: 8px;
    --btn-fs: 12px;
  }
  &.md {
    --btn-py: 8px;
    --btn-px: 16px;
    --btn-fs: 14px;
  }
  &.lg {
    --btn-py: 12px;
    --btn-px: 24px;
    --btn-fs: 16px;
  }
}
</style>
