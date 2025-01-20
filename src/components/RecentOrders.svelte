<script>
  // Example data – now with dynamically generated event avatars
  let orders = [
    {
      orderId: "#0912",
      dateOfPurchase: "Fri, Jul 26, 2024",
      event: {
        name: "Laugh Riot",
      },
      customer: {
        name: "Melissa Crew",
      },
      tickets: 6,
      channel: {
        name: "Instagram",
        icon: "https://upload.wikimedia.org/wikipedia/commons/e/e7/Instagram_logo_2016.svg",
      },
      total: 84,
    },
    {
      orderId: "#0122",
      dateOfPurchase: "Fri, Jul 26, 2024",
      event: {
        name: "Mister Vape Face",
      },
      customer: {
        name: "Anthony Brooke",
      },
      tickets: 3,
      channel: {
        name: "Twitter / X",
        icon: "https://upload.wikimedia.org/wikipedia/commons/9/9f/X_logo_2023.svg",
      },
      total: 72,
    },
    {
      orderId: "#02332",
      dateOfPurchase: "Thu, Jul 25, 2024",
      event: {
        name: "Punchline Parade",
      },
      customer: {
        name: "Kelly Levine",
      },
      tickets: 2,
      channel: {
        name: "Instagram",
        icon: "https://upload.wikimedia.org/wikipedia/commons/e/e7/Instagram_logo_2016.svg",
      },
      total: 48,
    },
  ];

  // Helper to generate UI Avatar URL dynamically
  function getAvatarUrl(name) {
    const encodedName = encodeURIComponent(name);
    return `https://ui-avatars.com/api/?name=${encodedName}&background=0D8ABC&color=FFFFFF&size=60`;
  }
</script>

<!-- Card Container -->
<div class="w-full rounded-xl py-4 px-6 flex flex-col mt-4 shadow-md bg-white">
  <!-- Header -->
  <div class="flex justify-between items-center mb-4">
    <span class="text-xl font-medium text-gray-800">Recent Orders</span>
    <div class="text-blue-400 cursor-pointer font-medium">Show all</div>
  </div>

  <!-- Responsive table wrapper -->
  <div class="overflow-x-auto">
    <table class="w-full min-w-max text-left">
      <!-- Table head -->
      <thead
        class="bg-gray-50 text-gray-500 uppercase text-xs border-b border-gray-200"
      >
        <tr>
          <th class="py-3 px-4 font-medium">ORDER ID</th>
          <th class="py-3 px-4 font-medium">DATE OF PURCHASE</th>
          <th class="py-3 px-4 font-medium">EVENT</th>
          <th class="py-3 px-4 font-medium">CUSTOMER</th>
          <th class="py-3 px-4 font-medium">NO. OF TICKETS</th>
          <th class="py-3 px-4 font-medium">SALES CHANNEL</th>
          <th class="py-3 px-4 font-medium">ORDER TOTAL</th>
        </tr>
      </thead>

      <!-- Table body -->
      <tbody class="divide-y divide-gray-200 text-sm">
        {#each orders as order}
          <tr>
            <!-- ORDER ID -->
            <td class="py-3 px-4 font-medium text-gray-700">
              {order.orderId}
            </td>

            <!-- DATE OF PURCHASE -->
            <td class="py-3 px-4 text-gray-700">
              {order.dateOfPurchase}
            </td>

            <!-- EVENT (Avatar + Name) -->
            <td class="py-3 px-4 text-gray-700">
              <div class="flex items-center space-x-2">
                <img
                  src={getAvatarUrl(order.event.name)}
                  alt={order.event.name}
                  class="w-8 h-8 object-cover rounded-full"
                />
                <span>{order.event.name}</span>
              </div>
            </td>

            <!-- CUSTOMER (Avatar + Name) -->
            <td class="py-3 px-4 text-gray-700">
              <div class="flex items-center space-x-2">
                <img
                  src={getAvatarUrl(order.customer.name)}
                  alt={order.customer.name}
                  class="w-8 h-8 object-cover rounded-full"
                />
                <span>{order.customer.name}</span>
              </div>
            </td>

            <!-- NO. OF TICKETS -->
            <td class="py-3 px-4 text-gray-700">
              {order.tickets}
            </td>

            <!-- SALES CHANNEL (icon + label) -->
            <td class="py-3 px-4 text-gray-700">
              <div class="flex items-center space-x-2">
                <img
                  src={order.channel.icon}
                  alt={order.channel.name}
                  class="w-5 h-5"
                />
                <span>{order.channel.name}</span>
              </div>
            </td>

            <!-- ORDER TOTAL -->
            <td class="py-3 px-4 font-semibold text-green-600">
              ${order.total}
            </td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</div>
