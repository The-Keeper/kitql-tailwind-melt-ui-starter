<script lang="ts">
  import { createSwitch } from '@melt-ui/svelte'
    export let checked = false
    export let disabled = false

    const { root, input, checked: checkedStore, isChecked } = createSwitch({
    disabled,
    checked
    })

    $: checkedStore.set(checked)
    checkedStore.subscribe((v) => (checked = v))
</script>


<form>
    <div class="flex items-center">
      <label class="pr-4 leading-none text-black dark:text-white" for="airplane-mode">
        Dark mode:          
      </label>
      <button
        melt={$root}
        class="relative h-6 w-11 cursor-default rounded-full bg-magnum-800 transition-colors data-[state=checked]:bg-magnum-950"
        id="airplane-mode"
      >
        <span
          class="block h-5 w-5 translate-x-0.5 rounded-full bg-white
                  transition-transform will-change-transform
                  {$isChecked && 'translate-x-[22px]'}"
        > 

    </span>
        <input melt={$input} />
      </button>
    </div>
  </form>