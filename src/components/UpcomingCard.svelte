<script>
  // Example data. Adjust or fetch dynamically as needed.
  let events = [
    {
      dateDay: "Fri",
      dateNum: 23,
      dateMonth: "Sep",
      name: "Jetpack Comedy",
      time: "12:30PM PST",
      capacityUsed: 875,
      capacityTotal: 1023,
      inCart: 2,
      price: 1482,
      avatars: [
        "https://ui-avatars.com/api/?name=John+Doe&background=0D8ABC&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Jane+Smith&background=F39C12&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Chris+Parker&background=E74C3C&color=FFFFFF&size=40",
      ],
    },
    {
      dateDay: "Fri",
      dateNum: 23,
      dateMonth: "Sep",
      name: "Adrenaline",
      time: "12:30PM PST",
      capacityUsed: 240,
      capacityTotal: 500,
      inCart: 2,
      price: 1482,
      avatars: [
        "https://ui-avatars.com/api/?name=Mark+Lee&background=2ECC71&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Olivia+Jones&background=3498DB&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Paul+Wilson&background=9B59B6&color=FFFFFF&size=40",
      ],
    },
    {
      dateDay: "Fri",
      dateNum: 23,
      dateMonth: "Sep",
      name: "The Reading Out of Your Notebook",
      time: "12:30PM PST",
      capacityUsed: 15,
      capacityTotal: 889,
      inCart: 2,
      price: 1482,
      avatars: [
        "https://ui-avatars.com/api/?name=Sarah+Wong&background=34495E&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Mike+Green&background=1ABC9C&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Emma+Hill&background=9B59B6&color=FFFFFF&size=40",
      ],
    },
    {
      dateDay: "Fri",
      dateNum: 23,
      dateMonth: "Sep",
      name: "Mister Vape Face Dies on Stage",
      time: "12:30PM PST",
      capacityUsed: 875,
      capacityTotal: 1023,
      inCart: 2,
      price: 1482,
      avatars: [
        "https://ui-avatars.com/api/?name=Carlos+Robles&background=E67E22&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Anna+Daniels&background=D35400&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Bob+Martin&background=BDc3C7&color=FFFFFF&size=40",
      ],
    },
    {
      dateDay: "Fri",
      dateNum: 23,
      dateMonth: "Sep",
      name: "The Nicole Show",
      time: "12:30PM PST",
      capacityUsed: 240,
      capacityTotal: 500,
      inCart: 2,
      price: 1482,
      avatars: [
        "https://ui-avatars.com/api/?name=Nicole+Garcia&background=F1C40F&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=David+Kim&background=7F8C8D&color=FFFFFF&size=40",
        "https://ui-avatars.com/api/?name=Sophie+Allen&background=F39C12&color=FFFFFF&size=40",
      ],
    },
  ];

  // Helper to choose progress-bar color based on capacity ratio
  function getBarColor(used, total) {
    const ratio = used / total;
    if (ratio > 0.7) return "bg-green-500";
    if (ratio > 0.3) return "bg-orange-400";
    return "bg-red-500";
  }
</script>

<div class="w-full rounded-xl py-4 px-6 flex flex-col mt-4 shadow-md">
  <div class="flex justify-between">
    <span class="text-xl">Upcoming Events</span>
    <div class="text-blue-400 cursor-pointer font-medium">Show all</div>
  </div>
  <div class="divide-y divide-gray-200 mt-4">
    {#each events as event, i}
      <div
        class="grid grid-cols-[auto_1fr_auto] gap-4 items-center content-center py-2"
      >
        <!-- Date block -->
        <div class="text-center leading-tight">
          <div class="uppercase text-xs text-gray-500">{event.dateDay}</div>
          <div class="text-xl font-bold text-blue-400">{event.dateNum}</div>
          <div class="uppercase text-xs text-gray-500">{event.dateMonth}</div>
        </div>

        <!-- Title/time block -->
        <div class="flex flex-col items-start space-y-1">
          <div class="">{event.name}</div>
          <div class="text-sm text-gray-500">{event.time}</div>
        </div>

        <!-- Right section: Avatars + Capacity bar + Price -->
        <div class="flex items-center space-x-4">
          <!-- Avatar stack -->
          <div class="flex -space-x-2">
            {#each event.avatars as avatar, idx}
              <img
                src={avatar}
                alt="Avatar"
                class="w-8 h-8 rounded-full border-2 border-white"
              />
            {/each}
            <!-- Example “+5” if you wanted to show a count -->
            <div
              class="w-8 h-8 flex items-center justify-center bg-gray-200 rounded-full text-sm font-medium border-2 border-white"
            >
              +5
            </div>
          </div>

          <!-- Capacity bar & info -->
          <div class="flex flex-col items-end">
            <div class="text-sm font-medium">
              {event.capacityUsed}/{event.capacityTotal}
            </div>
            <div class="w-24 h-2 bg-gray-200 rounded-full overflow-hidden">
              <div
                class={`h-full ${getBarColor(
                  event.capacityUsed,
                  event.capacityTotal
                )}`}
                style="width: {(event.capacityUsed / event.capacityTotal) *
                  100}%;"
              />
            </div>
            <div class="text-xs text-gray-500">{event.inCart} in cart</div>
          </div>

          <!-- Price -->
          <div class="text-green-600 text-lg font-semibold">
            ${event.price}
          </div>
        </div>
      </div>
    {/each}
  </div>
</div>
