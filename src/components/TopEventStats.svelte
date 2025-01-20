<script>
  // Data for the events
  const events = [
    {
      date: "Jan 19, 2020",
      title: "The Chronicles from Your Journal",
      value: 86,
    },
    { date: "Jan 20, 2020", title: "Insights from Your Diary", value: 75 },
    { date: "Jan 24, 2020", title: "The Stories in Your Scribbles", value: 59 },
    { date: "Feb 1, 2020", title: "Whispers from Your Pages", value: 40 },
    { date: "Jan 19, 2020", title: "The Secrets in Your Jotter", value: 36 },
  ];
</script>

<!-- Card Container -->
<div class="w-full rounded-xl py-4 px-6 shadow-md bg-white">
  <div class="flex justify-between items-center mb-4">
    <h2 class="text-lg font-medium text-gray-800">Top Events</h2>
    <div class="flex space-x-2">
      <button
        class="text-gray-500 px-3 py-1 border border-gray-300 rounded-md hover:bg-gray-100"
      >
        Ticket Sales
      </button>
      <button
        class="text-white bg-blue-500 px-3 py-1 border border-blue-500 rounded-md"
      >
        Revenue
      </button>
    </div>
  </div>
  <!-- List of Events -->
  <ul class="space-y-2">
    {#each events as event}
      <li
        class="flex items-center bg-opacity-50 rounded-lg px-4 py-3 relative overflow-hidden"
      >
        <div class="text-sm text-blue-600 w-32 z-10">{event.date}</div>

        <div class="text-sm text-gray-800 flex-grow z-10">{event.title}</div>

        <div class="text-sm text-blue-600 font-semibold z-10">
          {event.value}
        </div>
        <span
          class="bg-blue-100 left-0 absolute h-full"
          style="width: {event.value}%;"
        ></span>
      </li>
    {/each}
  </ul>
</div>

<style>
  /* Optional: If you want to customize further */
</style>
