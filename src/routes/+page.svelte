<script>
  import DashboardCard from "../components/DashboardCard.svelte";
  import NotificationPanel from "../components/NotificationPanel.svelte";
  import RecentOrders from "../components/RecentOrders.svelte";
  import RevenueChart from "../components/RevenueChart.svelte";
  import UpcomingCard from "../components/UpcomingCard.svelte";
  import TopEventStats from "../components/TopEventStats.svelte";
  import UnderPerformingStats from "../components/UnderPerformingStats.svelte";
</script>

<div
  class="w-full flex flex-col items-start justify-center border-b border-gray-200"
>
  <span class="text-xl">Dashboard</span>
  <span class="text-sm text-gray-500">Last 30 days</span>
</div>
<div class="grid grid-cols-[1fr_480px] gap-x-4 mt-4">
  <div class="">
    <div class="flex items-center gap-4">
      <DashboardCard />
      <DashboardCard />
      <DashboardCard />
    </div>
    <UpcomingCard />
    <RevenueChart />
    <RecentOrders />
  </div>
  <div class="space-y-4">
    <NotificationPanel />
    <TopEventStats />
    <UnderPerformingStats />
  </div>
</div>
