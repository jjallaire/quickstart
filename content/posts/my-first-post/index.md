---
title: "My First Post"
date: 2021-09-07T11:03:57-04:00
format: hugo
execute:
  echo: false
---



<script type="module" src="index_files/libs/quarto-ojs/esbuild-bundle.js"></script>
<link  href="index_files/libs/quarto-ojs/quarto-ojs.css" rel="stylesheet" />

## Inputs

<div class="cell">

``` js
viewof bill_length_min = Inputs.range(
  [32, 50], 
  {value: 35, step: 1, label: "Bill length (min):"}
)
viewof islands = Inputs.checkbox(
  ["Torgersen", "Biscoe", "Dream"], 
  { value: ["Torgersen", "Biscoe"], 
    label: "Islands:"
  }
)
```

<div class="cell-output-display">

<div>

<div id="ojs-cell-1-1" nodetype="declaration">

</div>

</div>

</div>

<div class="cell-output-display">

<div>

<div id="ojs-cell-1-2" nodetype="declaration">

</div>

</div>

</div>

</div>

## Plot

<div class="cell">

``` js
Plot.rectY(filtered, 
  Plot.binX(
    {y: "count"}, 
    {x: "body_mass", fill: "species", thresholds: 20}
  ))
  .plot({
    facet: {
      data: filtered,
      x: "sex",
      y: "species",
      marginRight: 80
    },
    marks: [
      Plot.frame(),
    ]
  }
)
```

<div class="cell-output-display">

<div id="ojs-cell-2" nodetype="expression">

</div>

</div>

</div>

## Data

<div class="cell">

``` js
Inputs.table(filtered)
```

<div class="cell-output-display">

<div id="ojs-cell-3" nodetype="expression">

</div>

</div>

</div>

<div class="cell">

``` js
data = FileAttachment("palmer-penguins.csv").csv({ typed: true })
```

<div class="cell-output-display">

<div id="ojs-cell-4" nodetype="declaration">

</div>

</div>

</div>

<div class="cell">

``` js
filtered = data.filter(function(penguin) {
  return bill_length_min < penguin.bill_length &&
         islands.includes(penguin.island);
})
```

<div class="cell-output-display">

<div id="ojs-cell-5" nodetype="declaration">

</div>

</div>

</div>

<!-- -->

<script type="ojs-module-contents">
{"contents":[{"methodName":"interpret","cellName":"ojs-cell-1","inline":false,"source":"viewof bill_length_min = Inputs.range(\n  [32, 50], \n  {value: 35, step: 1, label: \"Bill length (min):\"}\n)\nviewof islands = Inputs.checkbox(\n  [\"Torgersen\", \"Biscoe\", \"Dream\"], \n  { value: [\"Torgersen\", \"Biscoe\"], \n    label: \"Islands:\"\n  }\n)"},{"methodName":"interpret","cellName":"ojs-cell-2","inline":false,"source":"Plot.rectY(filtered, \n  Plot.binX(\n    {y: \"count\"}, \n    {x: \"body_mass\", fill: \"species\", thresholds: 20}\n  ))\n  .plot({\n    facet: {\n      data: filtered,\n      x: \"sex\",\n      y: \"species\",\n      marginRight: 80\n    },\n    marks: [\n      Plot.frame(),\n    ]\n  }\n)"},{"methodName":"interpret","cellName":"ojs-cell-3","inline":false,"source":"Inputs.table(filtered)"},{"methodName":"interpret","cellName":"ojs-cell-4","inline":false,"source":"data = FileAttachment(\"palmer-penguins.csv\").csv({ typed: true })"},{"methodName":"interpret","cellName":"ojs-cell-5","inline":false,"source":"filtered = data.filter(function(penguin) {\n  return bill_length_min < penguin.bill_length &&\n         islands.includes(penguin.island);\n})"},{"methodName":"interpretQuiet","source":"shinyInput('bill_length_min')"},{"methodName":"interpretQuiet","source":"shinyInput('islands')"}]}
</script>
<script type="module">
window._ojs.paths.runtimeToDoc = "../../..";
window._ojs.paths.runtimeToRoot = "../../..";
window._ojs.paths.docToRoot = "";
window._ojs.selfContained = false;
window._ojs.runtime.interpretFromScriptTags();
</script>
