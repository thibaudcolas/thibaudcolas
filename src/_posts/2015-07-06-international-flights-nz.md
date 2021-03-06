---
layout: post
title: International flights to and from New Zealand
date: 2015-07-06 18:40:02 +1200
comments: true
categories: [Dataviz, Open Data, Experiments, D3]
redirect_from:
  - /viz/international-flights-nz
---

This is [StatsNZ](http://www.stats.govt.nz/infoshare/SelectVariables.aspx?pxID=163d666b-55b3-476a-ba8b-d8507dd8b0e3) data about immigration in New Zealand. Worth having a look at!

<!-- more -->

> Flights are only counted if at least one individual on the flight is recorded as an arrival or a departure.
>
> Although most flights are scheduled commercial services, the numbers may also include charter services, private aircraft, cargo aircraft and other special flights.
>
> Flights may visit more than one overseas port, and will be counted under each. Hence, the sum across overseas ports may differ from the total number of flights.

<link rel="stylesheet" href="/assets/data/metricsgraphics.css">
<style>
.mg-line1-color { stroke: #393b79;} .mg-area1-color { fill: #393b79;} .mg-hover-line1-color { fill: #393b79;} .mg-line1-legend-color { color: #393b79;}
.mg-line2-color { stroke: #5254a3;} .mg-area2-color { fill: #5254a3;} .mg-hover-line2-color { fill: #5254a3;} .mg-line2-legend-color { color: #5254a3;}
.mg-line3-color { stroke: #6b6ecf;} .mg-area3-color { fill: #6b6ecf;} .mg-hover-line3-color { fill: #6b6ecf;} .mg-line3-legend-color { color: #6b6ecf;}
.mg-line4-color { stroke: #9c9ede;} .mg-area4-color { fill: #9c9ede;} .mg-hover-line4-color { fill: #9c9ede;} .mg-line4-legend-color { color: #9c9ede;}
.mg-line5-color { stroke: #637939;} .mg-area5-color { fill: #637939;} .mg-hover-line5-color { fill: #637939;} .mg-line5-legend-color { color: #637939;}
.mg-line6-color { stroke: #8ca252;} .mg-area6-color { fill: #8ca252;} .mg-hover-line6-color { fill: #8ca252;} .mg-line6-legend-color { color: #8ca252;}
.mg-line7-color { stroke: #b5cf6b;} .mg-area7-color { fill: #b5cf6b;} .mg-hover-line7-color { fill: #b5cf6b;} .mg-line7-legend-color { color: #b5cf6b;}
.mg-line8-color { stroke: #cedb9c;} .mg-area8-color { fill: #cedb9c;} .mg-hover-line8-color { fill: #cedb9c;} .mg-line8-legend-color { color: #cedb9c;}
.mg-line9-color { stroke: #8c6d31;} .mg-area9-color { fill: #8c6d31;} .mg-hover-line9-color { fill: #8c6d31;} .mg-line9-legend-color { color: #8c6d31;}
.mg-line10-color { stroke: #bd9e39;} .mg-area10-color { fill: #bd9e39;} .mg-hover-line10-color { fill: #bd9e39;} .mg-line10-legend-color { color: #bd9e39;}
.mg-line11-color { stroke: #e7ba52;} .mg-area11-color { fill: #e7ba52;} .mg-hover-line11-color { fill: #e7ba52;} .mg-line11-legend-color { color: #e7ba52;}
.mg-line12-color { stroke: #e7cb94;} .mg-area12-color { fill: #e7cb94;} .mg-hover-line12-color { fill: #e7cb94;} .mg-line12-legend-color { color: #e7cb94;}
.mg-line13-color { stroke: #843c39;} .mg-area13-color { fill: #843c39;} .mg-hover-line13-color { fill: #843c39;} .mg-line13-legend-color { color: #843c39;}
.mg-line14-color { stroke: #ad494a;} .mg-area14-color { fill: #ad494a;} .mg-hover-line14-color { fill: #ad494a;} .mg-line14-legend-color { color: #ad494a;}
.mg-line15-color { stroke: #d6616b;} .mg-area15-color { fill: #d6616b;} .mg-hover-line15-color { fill: #d6616b;} .mg-line15-legend-color { color: #d6616b;}
.mg-line16-color { stroke: #e7969c;} .mg-area16-color { fill: #e7969c;} .mg-hover-line16-color { fill: #e7969c;} .mg-line16-legend-color { color: #e7969c;}
.mg-line17-color { stroke: #7b4173;} .mg-area17-color { fill: #7b4173;} .mg-hover-line17-color { fill: #7b4173;} .mg-line17-legend-color { color: #7b4173;}
.mg-line18-color { stroke: #a55194;} .mg-area18-color { fill: #a55194;} .mg-hover-line18-color { fill: #a55194;} .mg-line18-legend-color { color: #a55194;}
.mg-line19-color { stroke: #ce6dbd;} .mg-area19-color { fill: #ce6dbd;} .mg-hover-line19-color { fill: #ce6dbd;} .mg-line19-legend-color { color: #ce6dbd;}
.mg-line20-color { stroke: #de9ed6;} .mg-area20-color { fill: #de9ed6;} .mg-hover-line20-color { fill: #de9ed6;} .mg-line20-legend-color { color: #de9ed6;}
.mg-line21-color { stroke: #3182bd;} .mg-area21-color { fill: #3182bd;} .mg-hover-line21-color { fill: #3182bd;} .mg-line21-legend-color { color: #3182bd;}
.mg-line22-color { stroke: #6baed6;} .mg-area22-color { fill: #6baed6;} .mg-hover-line22-color { fill: #6baed6;} .mg-line22-legend-color { color: #6baed6;}
.mg-line23-color { stroke: #9ecae1;} .mg-area23-color { fill: #9ecae1;} .mg-hover-line23-color { fill: #9ecae1;} .mg-line23-legend-color { color: #9ecae1;}
.mg-line24-color { stroke: #c6dbef;} .mg-area24-color { fill: #c6dbef;} .mg-hover-line24-color { fill: #c6dbef;} .mg-line24-legend-color { color: #c6dbef;}
.mg-line25-color { stroke: #e6550d;} .mg-area25-color { fill: #e6550d;} .mg-hover-line25-color { fill: #e6550d;} .mg-line25-legend-color { color: #e6550d;}
.mg-line26-color { stroke: #fd8d3c;} .mg-area26-color { fill: #fd8d3c;} .mg-hover-line26-color { fill: #fd8d3c;} .mg-line26-legend-color { color: #fd8d3c;}
.mg-line27-color { stroke: #fdae6b;} .mg-area27-color { fill: #fdae6b;} .mg-hover-line27-color { fill: #fdae6b;} .mg-line27-legend-color { color: #fdae6b;}
.mg-line28-color { stroke: #fdd0a2;} .mg-area28-color { fill: #fdd0a2;} .mg-hover-line28-color { fill: #fdd0a2;} .mg-line28-legend-color { color: #fdd0a2;}
.mg-line29-color { stroke: #31a354;} .mg-area29-color { fill: #31a354;} .mg-hover-line29-color { fill: #31a354;} .mg-line29-legend-color { color: #31a354;}
.mg-line30-color { stroke: #74c476;} .mg-area30-color { fill: #74c476;} .mg-hover-line30-color { fill: #74c476;} .mg-line30-legend-color { color: #74c476;}
.mg-line31-color { stroke: #a1d99b;} .mg-area31-color { fill: #a1d99b;} .mg-hover-line31-color { fill: #a1d99b;} .mg-line31-legend-color { color: #a1d99b;}
.mg-line32-color { stroke: #c7e9c0;} .mg-area32-color { fill: #c7e9c0;} .mg-hover-line32-color { fill: #c7e9c0;} .mg-line32-legend-color { color: #c7e9c0;}
.mg-line33-color { stroke: #756bb1;} .mg-area33-color { fill: #756bb1;} .mg-hover-line33-color { fill: #756bb1;} .mg-line33-legend-color { color: #756bb1;}
.mg-line34-color { stroke: #9e9ac8;} .mg-area34-color { fill: #9e9ac8;} .mg-hover-line34-color { fill: #9e9ac8;} .mg-line34-legend-color { color: #9e9ac8;}
.mg-line35-color { stroke: #bcbddc;} .mg-area35-color { fill: #bcbddc;} .mg-hover-line35-color { fill: #bcbddc;} .mg-line35-legend-color { color: #bcbddc;}
.mg-line36-color { stroke: #dadaeb;} .mg-area36-color { fill: #dadaeb;} .mg-hover-line36-color { fill: #dadaeb;} .mg-line36-legend-color { color: #dadaeb;}
.mg-line37-color { stroke: #636363;} .mg-area37-color { fill: #636363;} .mg-hover-line37-color { fill: #636363;} .mg-line37-legend-color { color: #636363;}
.mg-line38-color { stroke: #969696;} .mg-area38-color { fill: #969696;} .mg-hover-line38-color { fill: #969696;} .mg-line38-legend-color { color: #969696;}
.mg-line39-color { stroke: #bdbdbd;} .mg-area39-color { fill: #bdbdbd;} .mg-hover-line39-color { fill: #bdbdbd;} .mg-line39-legend-color { color: #bdbdbd;}
.mg-line40-color { stroke: #d9d9d9;} .mg-area40-color { fill: #d9d9d9;} .mg-hover-line40-color { fill: #d9d9d9;} .mg-line40-legend-color { color: #d9d9d9;}
</style>

<div id="inbound"></div>
<div id="inbound-legend"></div>
<div id="outbound"></div>
<div id="outbound-legend"></div>

<div id='total'></div>

<div id="inbound-rate"></div>
<div id="inbound-rate-legend"></div>

<script src="/assets/data/d3.min.js"></script>

<script src="/assets/data/jquery-2.1.4.min.js"></script>

<script src="/assets/data/metricsgraphics.min.js"></script>

<script src="/assets/data/international-flights-nz/script.js"></script>
