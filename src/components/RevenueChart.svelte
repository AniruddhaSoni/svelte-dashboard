<script>
  import { Chart, Spline, Axis, Grid, Svg } from "layerchart";
  import { scaleTime } from "d3-scale";

  // Define your data
  const data = [
    { date: "2025-01-01", totalRevenue: 5000, previousPeriod: 3000 },
    { date: "2025-01-05", totalRevenue: 8000, previousPeriod: 4000 },
    { date: "2025-01-10", totalRevenue: 25000, previousPeriod: 20000 },
    { date: "2025-01-15", totalRevenue: 10000, previousPeriod: 8000 },
    { date: "2025-01-20", totalRevenue: 20000, previousPeriod: 18000 },
    { date: "2025-01-25", totalRevenue: 15000, previousPeriod: 10000 },
    { date: "2025-01-31", totalRevenue: 30000, previousPeriod: 25000 },
  ];

  // Accessor functions
  const xAccessor = (d) => new Date(d.date);
  const yAccessorTotal = (d) => d.totalRevenue;
  const yAccessorPrevious = (d) => d.previousPeriod;

  // Date formatter for x-axis
  const formatDate = (date) =>
    date.toLocaleDateString("en-US", { month: "short", day: "numeric" });
</script>

<div class="w-full rounded-xl py-4 px-6 flex flex-col mt-4 shadow-md bg-white">
  <!-- Header -->
  <div class="flex justify-between items-center mb-4">
    <div>
      <h2 class="text-lg font-medium text-gray-800">Revenue</h2>
      <p class="text-sm text-gray-500">Last 30 days</p>
    </div>
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

  <!-- Chart Container -->
  <div class="h-[300px] p-4 border rounded">
    <Chart
      {data}
      x="date"
      xScale={scaleTime()}
      yDomain={[0, null]}
      padding={{ left: 40, bottom: 40 }}
    >
      <Svg>
        <!-- Grid Lines -->
        <Grid class="stroke-gray-200" />
        <!-- Left Axis -->
        <Axis
          placement="left"
          ticks={5}
          format={(d) => `$${d.toLocaleString()}`}
          class="stroke-gray-300"
        />
        <!-- Bottom Axis -->
        <Axis
          placement="bottom"
          format={(d) => formatDate(new Date(d))}
          class="stroke-gray-300"
        />
        <!-- Spline for Total Revenue -->
        <Spline y={yAccessorTotal} class="stroke-2 stroke-blue-500" />
        <!-- Spline for Previous Period -->
        <Spline
          y={yAccessorPrevious}
          class="stroke-2 stroke-blue-300 stroke-dasharray-5-5"
        />
      </Svg>
    </Chart>
  </div>
</div>
