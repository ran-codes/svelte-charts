<script>
  import ConclusionSection from './components/ConclusionSection.svelte';

  import LineChart from './charts/LineChart.svelte';
  import BarChart from './charts/BarChart.svelte';
  import ColumnChart from './charts/ColumnChart.svelte';
  import ScatterChart from './charts/ScatterChart.svelte';
  import MarkerChart from './charts/MarkerChart.svelte';
  import DotPlotChart from './charts/DotPlotChart.svelte';

  import data from './data/data';
  import dataScatter from './data/data-scatter';
  import dataTime from './data/data-time';

  import { timeFormat } from 'd3-time-format';

  // Chart options
  let animation = true;
  let hover = true;
  let hovered = null;
  let hoveredScatter = null;
  let select = true;
  let selected = null;
  let selectedScatter = null;
  let barchart1 = {
    options: ['apples', 'bananas', 'cherries', 'dates'],
    selected: 'apples',
  };
  let barchart2 = {
    options: ['stacked', 'comparison', 'barcode', 'grouped'],
    selected: 'stacked',
  };
  let linechart = {
    stacked: true,
    line: true,
    area: true,
    transparent: true,
  };
  let beeswarm = {
    yKey: false,
    zKey: false,
    rKey: true,
  };

  const doHover = (e) => (hovered = e.detail.id);
  const doSelect = (e) => (selected = e.detail.id);
  const doHoverScatter = (e) => (hoveredScatter = e.detail.id);
  const doSelectScatter = (e) => (selectedScatter = e.detail.id);
</script>

<section>
  <div class="wrapper">
    <h1>ONS Svelte Charts Library - Line Chart</h1>

    <div class="controls">
      <label
        ><input type="checkbox" bind:checked={animation} /> Animation enabled</label
      >
      <label
        ><input type="checkbox" bind:checked={hover} /> Hover events enabled</label
      >
      <label
        ><input type="checkbox" bind:checked={select} /> Select events enabled</label
      >
    </div>
  </div>
</section>

<section>
  <div class="grid">
    <div>
      <LineChart
        data={dataTime}
        xKey="year"
        yKey="value"
        zKey="group"
        color="grey"
        lineWidth={1}
        area={false}
        xScale="time"
        xFormatTick={(d) => timeFormat('%b %y')(d)}
        title="Line chart with time data"
        padding={{ top: 0, bottom: 20, left: 35, right: 60 }}
        {animation}
        legend
        labels
        {hover}
        {select}
      />
    </div>
  </div>
</section>

<style>
  section {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-pack: center;
    -ms-flex-pack: center;
    justify-content: center;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    margin: 0;
    margin-bottom: 20px;
    padding: 0;
  }
  .wrapper {
    width: 100%;
    max-width: 768px;
    margin: 0 16;
  }
  .grid {
    display: grid;
    width: 100%;
    max-width: 768px;
    margin: 0 16;
    grid-gap: 30px;
    grid-template-columns: repeat(auto-fit, minmax(min(280px, 100%), 1fr));
    justify-content: stretch;
  }
  h2 {
    font-size: 1.2em;
    font-weight: bold;
  }
  .controls > label {
    display: inline;
    margin-right: 8px;
  }
  .small {
    font-size: 0.8em;
  }
</style>
