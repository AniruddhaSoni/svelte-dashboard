<script>
  import { ArrowDownIcon, DollarSignIcon } from "svelte-feather-icons";
</script>

<div
  class="max-w-sm w-full h-20 flex px-8 py-4 shadow-md rounded-xl justify-between items-center"
>
  <div class="flex items-center">
    <div
      class="h-12 aspect-square grid place-items-center bg-green-300 rounded-md"
    >
      <DollarSignIcon class="text-green-600" />
    </div>
    <div class="flex flex-col items-start ml-2">
      <span class="text-gray-400">Revenue</span>
      <span class="text-2xl text-gray-700 font-medium"
        >$6,397<sup class="text-sm">97</sup>
      </span>
    </div>
  </div>
  <div class="text-red-400">
    <span class="font-bold text-lg flex items-center justify-center">
      <ArrowDownIcon class="text-red-400" strokeWidth={3} size="18" />
      3%</span
    >
  </div>
</div>
