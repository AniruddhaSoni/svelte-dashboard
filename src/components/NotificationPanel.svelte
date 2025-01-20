<script>
  const notifications = [
    {
      date: "Today",
      items: [
        {
          name: "Grace Lusk",
          action: "confirmed for",
          target: "Jest Quest",
          message: "“Can I go up early? I have another show at…”",
          time: "5 minutes ago",
          avatar:
            "https://ui-avatars.com/api/?name=Grace+Lusk&background=0D8ABC&color=FFFFFF&size=40",
          status: "success",
        },
        {
          name: "Andy Peters",
          action: "declined for",
          target: "Jest Quest",
          message: "",
          time: "21 minutes ago",
          avatar:
            "https://ui-avatars.com/api/?name=Andy+Peters&background=E74C3C&color=FFFFFF&size=40",
          status: "error",
        },
        {
          name: "All Performers",
          action: "confirmed for",
          target: "Jest Quest",
          message: "4/4 spots confirmed",
          time: "5 minutes ago",
          avatar:
            "https://ui-avatars.com/api/?name=Performers&background=1ABC9C&color=FFFFFF&size=40",
          status: "success",
        },
        {
          name: "Jest Quest",
          action: "has been published",
          target: "",
          message: "Ticket sales are now open",
          time: "5 minutes ago",
          avatar:
            "https://ui-avatars.com/api/?name=Jest+Quest&background=F39C12&color=FFFFFF&size=40",
          status: null,
        },
        {
          name: "Jetpack Comedy",
          action: "is sold out",
          target: "",
          message: "Ticket sales are now open",
          time: "5 minutes ago",
          avatar:
            "https://ui-avatars.com/api/?name=Jetpack+Comedy&background=F39C12&color=FFFFFF&size=40",
          status: null,
        },
      ],
    },
    {
      date: "Yesterday",
      items: [
        {
          name: "The Jetpack Comedy Show",
          action: "just sold out",
          target: "",
          message: "Thursday, 8:30pm",
          time: "",
          avatar:
            "https://ui-avatars.com/api/?name=Jest+Quest&background=F39C12&color=FFFFFF&size=40",
          status: null,
        },
        {
          name: "6 VIP tickets",
          action: "sold for",
          target: "The Black Lady Sketch Show",
          message: "85/100 sold",
          time: "Tuesday, 6:38pm",
          avatar:
            "https://ui-avatars.com/api/?name=Jest+Quest&background=F39C12&color=FFFFFF&size=40",
          status: null,
        },
      ],
    },
  ];
</script>

<div class="w-full rounded-xl py-4 px-6 flex flex-col shadow-md bg-white">
  <!-- Header -->
  <div class="flex justify-between items-center mb-4">
    <h2 class="text-lg font-medium text-gray-800">Notifications</h2>
    <a href="#" class="text-blue-500 text-sm font-medium">Show all</a>
  </div>

  <!-- Notifications List -->
  {#each notifications as section}
    <div>
      <!-- Section Header -->
      <p class="text-gray-500 text-xs font-semibold mb-2">{section.date}</p>

      <!-- Notifications -->
      <ul class="space-y-4">
        {#each section.items as notification}
          <li class="flex items-start">
            <!-- Avatar Container -->
            <div class="relative w-10 h-10">
              <img
                src={notification.avatar}
                alt={notification.name}
                class="w-10 h-10 rounded-full"
              />

              <!-- Status Icon -->
              {#if notification.status}
                <div
                  class={`absolute -bottom-1 -right-1 w-4 h-4 flex items-center justify-center rounded-full ${
                    notification.status === "success"
                      ? "bg-green-500"
                      : "bg-red-500"
                  }`}
                >
                  <span
                    class="text-white text-xs font-bold flex items-center justify-center"
                  >
                    {notification.status === "success" ? "✔" : "✖"}</span
                  >
                </div>
              {/if}
            </div>

            <!-- Details -->
            <div class="flex flex-col space-y-1 ml-4">
              <p class="text-sm text-gray-800">
                <span class="font-semibold">{notification.name}</span>
                {notification.action}{" "}
                <span class="font-semibold text-blue-500"
                  >{notification.target}</span
                >
              </p>
              {#if notification.message}
                <p class="text-xs text-gray-500">{notification.message}</p>
              {/if}
              {#if notification.time}
                <p class="text-xs text-gray-400">{notification.time}</p>
              {/if}
            </div>
          </li>
        {/each}
      </ul>
    </div>
  {/each}
</div>
