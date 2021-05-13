---
layout: redirects
permalink: /hosted/one-health/
---
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<meta name="viewport" content="initial-scale=1, maximum-scale=1,user-scalable=no">
<title>One Health Infographic</title>
<style>
html, body, #layoutNode { padding: 0px; margin: 0px; height: 100%; overflow: hidden; font-size: 13px; font-family: "Avenir Next"; }
</style>
<link href="https://bao.arcgis.com/InfographicsPlayer/BAMobile/8.4/reportPlayer/esri/themes/light/main.css" rel="stylesheet" />
<script>

    var dojoConfig = dojoConfig || {};
    dojoConfig.baseUrl = "https://bao.arcgis.com/InfographicsPlayer/BAMobile/8.4/reportPlayer/dojo";
  
</script>
<script src="https://bao.arcgis.com/InfographicsPlayer/BAMobile/8.4/reportPlayer/reportPlayer.js"></script>
<script>

  function init() {
    require([
        "esri/config",
        "esri/core/has",
        "esri/widgets/geoenrichment/ReportPlayer/ReportPlayer",
        "esri/widgets/geoenrichment/utils/JsonCompressor",
        "esri/widgets/geoenrichment/utils/UrlUtil",
        "esri/widgets/geoenrichment/ReportPlayer/dataProvider/commands/dynamic/FeatureServiceDataLoader"
    ],
    function (
        config,
        has,
        ReportPlayer,
        JsonCompressor,
        UrlUtil,
        FeatureServiceDataLoader
    ) {
        config.request.proxyUrl = UrlUtil.getUrlVariableValue(window.location.href, "proxy") || config.request.proxyUrl || null;
        FeatureServiceDataLoader.enrichReportDataWithFeatureServiceData(reportDataJson, function () {
          var player = new ReportPlayer({
            exportCommands: ["print", "create-image"],
            viewMode: UrlUtil.getUrlVariableValue(window.location.href, "viewMode") || "full-pages",
            enableDataDrilling: true
          }).placeAt(playerNode);
          player.on("error", function (error) { 
              console.error(error);
          });
          player.reportDataFromJSON(reportDataJson);
        });
    });
  }
  document.readyState === "complete" ? init() : document.onreadystatechange = () => document.readyState ==
      "complete" && init();

</script>
</head>
<body class="claro" style="margin:0px;">
<div id="playerNode"></div>
</body>
</html>