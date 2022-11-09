<template>
  <modal tabindex="-1" role="dialog">
    <form
      @keydown="handleKeydown"
      autocomplete="off"
      class="bg-white rounded-lg shadow-lg overflow-hidden w-action-fields"
    >
      <div>
        <h2 class="border-b border-40 py-8 px-8 text-90 font-normal text-xl">
          {{ __("Personal Access Token") }}
        </h2>
        <div>
          <div class="action">
            <div class="flex flex-col border-b border-40">
              <div class="flex items-center py-6 px-8">
                <slot></slot>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="bg-30 px-6 py-3 flex">
        <div class="flex items-center ml-auto">
          <button
            dusk="confirm-action-button"
            type="submit"
            class="btn btn-default btn-primary"
          >
            {{ __(`Confirm`) }}
          </button>
        </div>
      </div>
    </form>
  </modal>
</template>

<script>
export default {
  /**
   * Mount the component.
   */
  mounted() {
    document.querySelectorAll(".modal input")[0].focus()
  },
  methods: {
    /**
     * Stop propogation of input events unless it's for an escape or enter keypress
     */
    handleKeydown(e) {
      if (["Escape", "Enter"].indexOf(e.key) !== -1) {
        return
      }
      e.stopPropagation()
    },
    /**
     * Execute the selected action.
     */
    handleConfirm() {
      this.$emit("confirm")
    },
  },
}
</script>
