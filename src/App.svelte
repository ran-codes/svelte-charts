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
    <h1>ONS Svelte Charts Library</h1>
    <p>
      Below are a series of charts built using <a
        href="https://layercake.graphics"
        target="_blank">Layer Cake</a
      >, a responsive charts/graphics framework for
      <a href="https://svelte.dev" target="_blank">Svelte</a>. The charts are
      all responsive in that they fit to the width of their html container
      element, and will resize automatically when the screen/window is resized.
      The charts below can be used in the following ways:
    </p>
    <ol>
      <li>
        The charts and/or their sub-components (axes etc) can be <strong
          >imported into Svelte projects</strong
        > via NPM.
      </li>
      <li>
        The charts also have compiled versions that can be <strong
          >embedded in "vanilla" javascript projects</strong
        >.
      </li>
      <li>
        This whole repository can be <strong
          >downloaded/cloned and hacked</strong
        > to create variations of the charts.
      </li>
    </ol>
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
      <ColumnChart
        data={data.filter((d) => d.group == barchart1.selected)}
        xKey="year"
        yKey="value"
        title="Single variable column chart"
        {hover}
        {hovered}
        on:hover={doHover}
        {select}
        {selected}
        on:select={doSelect}
        {animation}
      >
        <div slot="options" class="controls small">
          {#each barchart1.options as option}
            <label
              ><input
                type="radio"
                bind:group={barchart1.selected}
                value={option}
              />
              {option}</label
            >
          {/each}
        </div>
      </ColumnChart>
    </div>
    <div>
      <ColumnChart
        {data}
        xKey="year"
        yKey="value"
        zKey="group"
        mode={barchart2.selected}
        title="Stacked / comparative column chart"
        {hover}
        {hovered}
        on:hover={doHover}
        {select}
        {selected}
        on:select={doSelect}
        {animation}
        legend
      >
        <div slot="options" class="controls small">
          {#each barchart2.options as option}
            <label
              ><input
                type="radio"
                bind:group={barchart2.selected}
                value={option}
              />
              {option}</label
            >
          {/each}
        </div>
      </ColumnChart>
    </div>
  </div>
</section>

<ConclusionSection />

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
