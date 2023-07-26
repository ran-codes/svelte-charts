<section>
  <div class="wrapper">
    <h2>Current features</h2>
    <p>
      In all use cases, each top-level chart component (eg. bar chart, scatter
      chart) is able to take a series of parameters (data, colours, title, etc)
      to initialise and customise it.
    </p>
    <p>
      As far as possible these parameters are consistent across chart types, and
      generally there are sensible default values for all parameters (eg. height
      = 300 pixels) other than "data", which always requires a Tidy Data array.
    </p>
    <h2>Examples of usage</h2>
    <p>
      You can see examples of how these charts can be used in a Svelte project
      in <a
        href="https://svelte.dev/repl/324b696de5304ceebbe0213511e7ed23?version=3.41.0"
        target="_blank">this REPL</a
      >, and how they can be used in a plain/vanilla javascript project in
      <a href="https://codepen.io/bothness/pen/RwVJvav" target="_blank"
        >this CodePen</a
      >.
    </p>
    <h2>Intended features</h2>
    <p>
      It is the intention to translate all of the most useful charts from Layer
      Cake's examples into components, as well as a number of other custom
      charts (eg. spine charts). For each of the charts, it is the intention to
      support the following functionalities:
    </p>
    <ul>
      <li>Every chart type to support a standard Tidy Data format.</li>
      <li>
        Optional title, legend and footnote types that can be added to charts.
      </li>
      <li>
        Optional hover and click-to-select functionality on all relevant chart
        types with custom events.
      </li>
      <li>Options/methods for inline labels, tooltips and annotations.</li>
      <li>Optional prefixes and suffixes for axis labels.</li>
      <li>
        Colour by group (z parameter) with colors = [array], and colours for
        hovered and highlighted/selected data points.
      </li>
      <li>
        Animated transitions when data or keys change (which can be
        enabled/disabled with animation = true/false).
      </li>
      <li>
        To group similar charts in a logical way to improve ease of use and
        allow for custom combinations and animated transitions (eg. scatter +
        beeswarm or line + area).
      </li>
      <li>
        Possibility to add custom LayerCake SVG/HTML/Canvas layers in front or
        behind standard layers of any chart.
      </li>
      <li>Support for pre-rendering and progressive enhancement.</li>
    </ul>
    <h2>Acknowledgement</h2>
    <p>
      These charts are largely based on the chart examples by <a
        href="https://twitter.com/mhkeller"
        target="
			_blank">Michael Keller</a
      >, the author of the Layer Cake charts/graphics framework for Svelte.
    </p>
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
