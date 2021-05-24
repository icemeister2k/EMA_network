# EMA_network
conditional probability network

zur Navigation: <a href="https://htmlpreview.github.io/?https://github.com/icemeister2k/EMA_network/blob/main/Navigation.html" target="_blank">---> LINK <---</a>

  <!DOCTYPE HTML>
<html>



<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1" /> 
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script src="https://visjs.github.io/vis-network/standalone/umd/vis-network.min.js"></script>
    <script src="https://canvasjs.com/assets/script/canvasjs.min.js"></script>
    <style>
        html,
        body {
            font: 20px arial;
            padding-left: 5%;
            padding-right: 5%;
        }

        #mynetwork {
            width: 100%;
            height: 500px;
            border: 1px solid lightgray;
        }

        #img {
            width: 100%;
            padding-left: 0%;
        }
        #img2 {
            width: 100%;
            padding-left: 0%;
        }

        button {
            background-color: #919a92;
            border: none;
            color: rgb(0, 0, 0);
            padding: 20px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            font-family: arial;
            margin: 7px 7px;
            cursor: pointer;

        }

        button:hover {
            background-color: #008CBA;
            color: white;
            font-family: arial;
        }

        button:active {
            border: 2px solid rgb(0, 128, 119);
            font-size: 20px;
            font-weight: bold;
            font-family: arial;
            color: white;
        }

        button:focus {
            background: rgb(0, 0, 0);
            font-size: 20px;
            font-family: arial;
            font-weight: bold;
            color: white;
        }

        #big {
            font-size: 25px;
            font-weight: bold;
            font-family: arial;
        }

        #small {
            font-size: 25px;
            font-family: arial;
            /* font-weight: bold; */
        }

        #divhighlight {
            background: rgb(198, 198, 198, 0.5);
        }

        p {
            font-size: 25px;
            font-family: arial;
        }

        #info {
            font-weight: normal;
        }
    </style>
    <script>


        function overall() {
            document.getElementById("info").innerText = "Aktuelles Dataset: Alle schweren Nebenwirkungen in der European Economic Area";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/overall_1.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }

            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_all.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });

            var imgg = document.createElement('img');
            imgg.src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/overall.svg";
            imgg.id = "img2";
            var img1 = document.querySelector('#img1');
            img1.appendChild(imgg);
        }
        function kids() {
            document.getElementById("info").innerText = "Aktuelles Dataset: Kinder (0-17 Jahre)";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/kids_overview.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }

            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_kids.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });

            var imgg = document.createElement('img');
            imgg.src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/kids_pie.svg";
            imgg.id = "img2";
            var img1 = document.querySelector('#img1');
            img1.appendChild(imgg);
        }
        function astra() {
            document.getElementById("info").innerText = "Aktuelles Dataset: Astra se neca";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/astra.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }
            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_astra.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });

        }
        function pfizer() {
            document.getElementById("info").innerText = "Aktuelles Dataset: Pfizer";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/pfizer.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }
            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_pfizer.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });

        }
        function moderna() {
            document.getElementById("info").innerText = "Aktuelles Dataset: Moderna";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/moderna.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }
            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_moderna.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });
        }
        function jj() {

            document.getElementById("info").innerText = "Aktuelles Dataset: j&j";
            document.getElementById("img").src = "https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/jj.svg";

            if (document.querySelector('#img2') !== null) {
                var dest = document.querySelector('#img2');
                dest.parentNode.removeChild(dest);
            }
            // $.getJSON("https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_kids.json", function (result) {
            //     return result;
            // }).then(function (result) {
            //     redrawAll(result[1], result[0]);
            // });
            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_kids.json')
                .then(response => response.json())
                .then(data => { redrawAll(data[1], data[0]) });


        }

        function drawBars(to, fr, title) {

            var chart = new CanvasJS.Chart("chartContainer", {
                animationEnabled: true,
                title: {
                    text: "Node: " + title,
                    fontFamily: "calibri"
                },
                axisY: {
                    title: "Wahrscheinlichkeit [%]",
                    gridColor: "black",
                    fontFamily: "calibri",
                    gridThickness: 0,
                    minimum: 0,
                },
                axisX: {
                    // labelAngle: 45,
                    // labelWrap: true,
                    labelAutoFit: true,
                    interval: 1,
                    // labelFontSize: 20,
                    // labelMaxWidth: 100,

                    labelFontColor: "black"
                },
                toolTip: {
                    shared: true,
                    fontFamily: "calibri"
                },
                legend: {
                    cursor: "pointer",
                    fontFamily: "calibri",
                    itemclick: toggleDataSeries,
                    fontSize: 30,
                    verticalAlign: "top",
                    horizontalAlign: "center",
                    cursor: "pointer",
                },
                data: [{
                    type: "column",
                    name: "Wenn " + title + " dann auch Symptom mit einer Wahrscheinlichkeit von: ",
                    color: "rgba(192, 26, 17, 1)",
                    legendText: "P(B|A)",
                    showInLegend: true,
                    dataPoints: fr
                }, {
                    type: "column",
                    name: "Wenn Symptom, dann auch " + title + " mit einer Wahrscheinlichkeit von: ",
                    color: "rgba(100, 51, 255, 1)",
                    legendText: "P(A|B)",
                    showInLegend: true,
                    dataPoints: to
                }
                ]

                // 
            });
            chart.render();

        }

        function toggleDataSeries(e) {
            if (typeof (e.dataSeries.visible) === "undefined" || e.dataSeries.visible) {
                e.dataSeries.visible = false;
            }
            else {
                e.dataSeries.visible = true;
            }
            chart.render();
        }



        var network;
        var allNodes;
        var highlightActive = false;
        function redrawAll(nodeDataset, edgeDataset) {
            var nodesDataset = new vis.DataSet(nodeDataset);
            var edgesDataset = new vis.DataSet(edgeDataset);
            var container = document.getElementById("mynetwork");
            var options = {
                nodes: {
                    shape: "dot",
                    scaling: {
                        min: 20,
                        max: 35,
                        label: {
                            min: 25,
                            max: 55,
                            // drawThreshold: 12,
                            // maxVisible: 20,
                        },
                    },
                    font: {
                        size: 14,
                        face: "Tahoma",
                    },
                },
                edges: {
                    // width: 0.15,
                    arrows: {
                        to: true
                    },
                    color: {
                        color: "rgba(188, 188, 188, 0.3)",
                        highlight: "rgba(100, 51, 255, 1)",
                        hover: "rgba(0, 0, 0, 1)",
                        inherit: "to"
                    },
                    smooth: {
                        type: "continuous",
                    },
                },
                physics: {
                    forceAtlas2Based: {
                        gravitationalConstant: -800,
                        centralGravity: 0.009,
                        springLength: 120,
                        springConstant: 0.18,
                        avoidOverlap: 1.5
                    },
                    maxVelocity: 146,
                    solver: 'forceAtlas2Based',
                    timestep: 0.35,
                    stabilization: {
                        enabled: true,
                        iterations: 2000,
                        updateInterval: 25
                    }
                },
                interaction: {
                    tooltipDelay: 200,
                    hideEdgesOnDrag: true,
                    hideEdgesOnZoom: true,
                },
            };
            var data = { nodes: nodesDataset, edges: edgesDataset }; // Note: data is coming from ./datasources/WorldCup2014.js

            network = new vis.Network(container, data, options);

            // get a JSON object
            allNodes = nodesDataset.get({ returnType: "Object" });
            allEdges = edgesDataset.get({ returnType: "Object" });
            network.on("stabilizationIterationsDone", function () {
                network.setOptions({ physics: false });
            });

            network.on("click", neighbourhoodHighlight);

            function neighbourhoodHighlight(params) {
                // if something is selected:
                if (params.nodes.length > 0) {
                    highlightActive = true;
                    var i, j;
                    var selectedNode = params.nodes[0];
                    var degrees = 2;

                    // mark all nodes as hard to read.
                    for (var nodeId in allNodes) {
                        allNodes[nodeId].color = "rgba(200,200,200,0.2)";
                        if (allNodes[nodeId].hiddenLabel === undefined) {
                            allNodes[nodeId].hiddenLabel = allNodes[nodeId].label;
                            allNodes[nodeId].label = undefined;
                        }
                    }
                    var connectedNodes = network.getConnectedNodes(selectedNode);
                    var allConnectedNodes = [];

                    var connectedEdges = network.getConnectedEdges(selectedNode);
                    // console.log(allEdges[connectedEdges[0]]);

                    json_to_filter = [];
                    for (j = 0; j < connectedEdges.length; j++) {
                        json_to_filter.push({ to: String(allEdges[connectedEdges[j]].tnode), from: String(allEdges[connectedEdges[j]].fnode), y: parseFloat(allEdges[connectedEdges[j]].value), id_to: allEdges[connectedEdges[j]].to, id_from: allEdges[connectedEdges[j]].from })
                    }

                    // filter by selected node for grouped column graph
                    var selectednode_df = json_to_filter.filter(a => a.id_from == selectedNode);
                    var connectednodes_df = json_to_filter.filter(a => a.id_from !== selectedNode);

                    fr = [];
                    tos = [];
                    tit = "";
                    if (typeof (selectednode_df[0]) !== "undefined") {
                        for (var k = 0; k < selectednode_df.length; k++) {
                            fr.push({ label: String(selectednode_df[k].to), y: parseFloat(selectednode_df[k].y * 100) });
                        }
                        tit = selectednode_df[0].from;
                    }
                    if (typeof (connectednodes_df[0]) !== "undefined") {
                        for (var k = 0; k < connectednodes_df.length; k++) {
                            tos.push({ label: String(connectednodes_df[k].from), y: parseFloat(connectednodes_df[k].y * 100) });
                        }
                        tit = connectednodes_df[0].to;
                    }

                    drawBars(tos, fr, tit);

                    // all first degree nodes get their own color and their label back
                    for (i = 0; i < connectedNodes.length; i++) {
                        allNodes[connectedNodes[i]].color = "rgba(100, 51, 255, 1)";
                        //console.log(allNodes[connectedNodes[i]]);
                        if (allNodes[connectedNodes[i]].hiddenLabel !== undefined) {
                            allNodes[connectedNodes[i]].label =
                                allNodes[connectedNodes[i]].hiddenLabel;
                            allNodes[connectedNodes[i]].hiddenLabel = undefined;
                        }
                    }

                    // the main node gets its own color and its label back.
                    allNodes[selectedNode].color = "rgba(192, 26, 17, 1)";
                    if (allNodes[selectedNode].hiddenLabel !== undefined) {
                        allNodes[selectedNode].label = allNodes[selectedNode].hiddenLabel;
                        allNodes[selectedNode].hiddenLabel = undefined;
                    }
                } else if (highlightActive === true) {
                    // reset all nodes
                    for (var nodeId in allNodes) {
                        allNodes[nodeId].color = "rgba(65, 173, 211, 1)";
                        if (allNodes[nodeId].hiddenLabel !== undefined) {
                            allNodes[nodeId].label = allNodes[nodeId].hiddenLabel;
                            allNodes[nodeId].hiddenLabel = undefined;
                        }
                    }
                    highlightActive = false;
                }

                // transform the object into an array
                var updateArray = [];
                for (nodeId in allNodes) {
                    if (allNodes.hasOwnProperty(nodeId)) {
                        updateArray.push(allNodes[nodeId]);
                    }
                }
                nodesDataset.update(updateArray);
            }


        }
        // $.getJSON("https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_kids.json", function (result) {
        //     return result;
        // }).then(function (result) {
        //     redrawAll(result[1], result[0]);
        // });



        window.onload = function () {
            fetch('https://raw.githubusercontent.com/icemeister2k/EMA_network/main/networkdata/network_all.json')
                .then(response => response.json())
                .then(data => redrawAll(data[1], data[0]));
        }





    </script>

</head>

<body>
    <h1>1. interaktives conditional probability network </h1>
    <div id="divhighlight">
        <p id="small">Top100 Symptome von Geimpften mit schweren Nebenwirkungen(Hospitalization/Disabling/Death/Fatal)</p>
        <p id="big">Dataset wechseln:<button onclick="overall()">Overall</button><button
                onclick="kids()">Kinder</button><button onclick="astra()">Astra</button><button
                onclick="pfizer()">Pfizer</button><button onclick="moderna()">Moderna</button><button
                onclick="jj()">J&J</button>

        </p>
    </div>

    <h2 id="info">Aktuelles Dataset: European Economic Area</h2>
    <p id="small">Auf nodes klicken für mehr Infos</p>
    <div id="mynetwork"></div>
    <div id="chartContainer" style="height: 600px; width: 100%"></div>
    <hr>
    <h1>2. Plots</h1>
    <div id="img1"><img id="img" src="https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/overall_1.svg"><img id="img2" src="https://raw.githubusercontent.com/icemeister2k/EMA_network/main/img/overall.svg"></div>
    <hr>
    <h1>3. Quellen & Methoden</h1>
    <p><b>Datenquellen:</b><br><br>Impfnebenwirkungen: <a href="https://www.adrreports.eu/en/" target="_blank">EMA
            Datenbank</a><br>Covid19 Tote und Impfungen pro Tag: <a
            href="https://github.com/owid/covid-19-data/tree/master/public/data" target="_blank">ourworldindata.org -
            github repo</a><br><br>
        <b>Methoden:</b><br><br><b>network:</b><br>1. Dataset wurde erst nach Diagnose-keywords gefiltert
        (Hospitalization/Disabling/Death/Fatal), anschließend nach dem Alter (Kinder Dataset) bzw. nach Vakzin in
        weitere Sets aufgeteilt<br><br>2. Aus dem gefilterten Set wurden einzigartige Diagnose-keywords extrahiert, das
        Set nach den erhaltenen einzigartigen keywords aggregiert, das resultierende Set nach Häufigkeit pro Symptom
        sortiert und daraus die 126 häufigsten Symptome extrahiert.<br><br>3. Das ursprüngliche gefilterte Set wurde
        nach Häufigkeit der erhaltenen top100 Symptome gefiltert und daraus die jeweiligen Wahrscheinlichkeiten ( =P(A)
        = ein node im Graph) berechnet. Die nodes sind größer dargestellt je größer die generelle Häufigkeit eines
        Symptoms P(A).
        <br><br>4. die Verbindungen zwischen den nodes (edges) wurden berechnet indem das ursprüngliche gefilterte Set
        erst nach dem jeweiligen Symptom (Top100) gefiltert wurde und daraus wurde nach dem gleichzeitigen Vorhandensein
        der 99 übrigen Symptome das jeweilige conditional probability P(B|A) berechnet. Wenn p(B|A) größer als 10% war
        wurde die jeweilige Verbindung in das resultierende network integriert.
    </p>



</body>

</html>
