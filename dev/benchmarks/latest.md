## Minecraft load time benchmark


---

<p align="center" style="font-size:160%;">
MC total load time:<br>
528.47 sec
<br>
<sup><sub>(
8:48 min
)</sub></sup>
</p>

<br>


<p align="center">
<img src="https://quickchart.io/chart?w=400&h=30&c={
  type: 'horizontalBar',
  data: {
    datasets: [
      {label:      'MODS:', data: [312.39]},
      {label: 'FML stuff:', data: [216.08]}
    ]
  },
  options: {
    scales: {
      xAxes: [{display: false,stacked: true}],
      yAxes: [{display: false,stacked: true}],
    },
    elements: {rectangle: {borderWidth: 2}},
    legend: {display: false,},
    plugins: {datalabels: {color: 'white',formatter: (value, context) =>
      [context.dataset.label, value].join(' ')
    }}
  }
}"/>
</p>

<br>

# Mods Loading Time
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=300&c={
  type: 'outlabeledPie',
  options: {
    cutoutPercentage: 25,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v,i)=>[
          v.labels[v.dataIndex],' ',
          (v.percent*1000|0)/10,
          String.fromCharCode(37)].join('')
      }
    }
  },
  data: {...
`
436e17  24.70s Had Enough Items;
3C6315  15.23s Had Enough Items (Plugins);
9e2174   2.44s Tinkers' Construct;
8E1E68  23.26s Tinkers' Construct (Oredict Melting);
813e81  12.97s OpenComputers;
516fa8  11.38s Ender IO;
5161a8   0.71s CraftTweaker2;
495797   8.66s CraftTweaker2 (Script Loading);
a651a8   8.85s IndustrialCraft 2;
8f3087   8.55s Forge Mod Loader;
8f304e   6.94s Astral Sorcery;
cd922c   6.12s NuclearCraft;
8c2ccd   5.78s Immersive Engineering;
213664   5.05s Forestry;
6e175e   4.95s Recurrent Complex;
538f30   4.09s Animania;
308f53   4.00s Village Names;
a86e51   3.75s Extra Utilities 2;
436e17   3.61s Integrated Dynamics;
8f4d30   3.56s Open Terrain Generator;
308f7e   3.37s Quark: RotN Edition;
ba3eb8   3.26s Cyclic;
649e21   3.05s OpenBlocks;
444444  71.70s 40 Other mods;
333333  59.04s 171 'Fast' mods (load 1.0s - 0.1s);
222222   7.37s 213 'Instant' mods (load %3C 0.1s)
`
    .split(';').reduce((a, l) => {
      l.match(/(\w{6}) *(\d*\.\d*)s (.*)/)
      .slice(1).map((a, i) => [[String.fromCharCode(35),a].join(''), parseFloat(a), a][i])
      .forEach((s, i) => 
        [a.datasets[0].backgroundColor, a.datasets[0].data, a.labels][i].push(s)
      );
      return a
    }, {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 1
      }]
    })
  }
}"/>
</p>

<br>

# Top Mods Details (except JEI, FML and Forge)
<p align="center">
<img src="https://quickchart.io/chart?w=400&h=450&c={
  options: {
    scales: {
      xAxes: [{stacked: true}],
      yAxes: [{stacked: true}],
    },
    plugins: {
      datalabels: {
        anchor: 'end',
        align: 'top',
        color: 'white',
        backgroundColor: 'rgba(46, 140, 171, 0.6)',
        borderColor: 'rgba(41, 168, 194, 1.0)',
        borderWidth: 0.5,
        borderRadius: 3,
        padding: 0,
        font: {size:10},
        formatter: (v,ctx) => 
          ctx.datasetIndex!=ctx.chart.data.datasets.length-1 ? null
            : [((ctx.chart.data.datasets.reduce((a,b)=>a- -b.data[ctx.dataIndex],0)*10)|0)/10,'s'].join('')
      },
      colorschemes: {
        scheme: 'office.Damask6'
      }
    }
  },
  type: 'bar',
  data: {...(() => {
    let a = { labels: [], datasets: [] };
`
1: Construction;
2: Loading Resources;
3: PreInitialization;
4: Initialization;
5: InterModComms$IMC;
6: PostInitialization;
7: LoadComplete;
8: ModIdMapping
`
    .split(';')
      .map(l => l.match(/\d: (.*)/).slice(1))
      .forEach(([name]) => a.datasets.push({ label: name, data: [] }));
`
                          1      2      3      4      5      6      7      8  ;
Tinkers' Construct    |  1.04|  0.01|  0.21|  0.06|  0.00| 24.39|  0.00|  0.00;
OpenComputers         |  0.19|  0.02|  9.55|  3.03|  0.19|  0.00|  0.00|  0.00;
Ender IO              |  1.66|  0.01|  3.84|  0.52|  3.28|  1.16|  0.00|  0.90;
CraftTweaker2         |  0.65|  0.00|  4.02|  0.01|  0.00|  4.69|  0.01|  0.00;
IndustrialCraft 2     |  0.77|  0.02|  6.92|  0.89|  0.00|  0.26|  0.00|  0.00;
Astral Sorcery        |  0.23|  0.01|  4.61|  1.60|  0.00|  0.50|  0.00|  0.00;
NuclearCraft          |  0.56|  0.01|  3.92|  0.37|  0.00|  1.21|  0.00|  0.05;
Immersive Engineering |  0.84|  0.01|  1.77|  0.96|  0.00|  2.20|  0.00|  0.00;
Forestry              |  0.41|  0.01|  3.26|  0.94|  0.00|  0.42|  0.00|  0.00;
Recurrent Complex     |  0.26|  0.01|  0.69|  0.90|  0.00|  3.10|  0.00|  0.00;
Animania              |  0.33|  0.00|  3.19|  0.10|  0.00|  0.47|  0.00|  0.00;
Village Names         |  0.12|  0.00|  3.69|  0.19|  0.00|  0.00|  0.00|  0.00
`
    .split(';').slice(1)
      .map(l => l.split('|').map(s => s.trim()))
      .forEach(([name, ...arr], i) => {
        a.labels.push(name);
        arr.forEach((v, j) => a.datasets[j].data[i] = v)
      }); return a
  })()}
}"/>
</p>

<br>

# TOP JEI Registered Plugis
<p align="center">
<img src="https://quickchart.io/chart?w=700&c={
  options: {
    elements: { rectangle: { borderWidth: 1 } },
    legend: false
  },
  type: 'horizontalBar',
    data: {...(() => {
      let a = {
        labels: [], datasets: [{
          backgroundColor: 'rgba(0, 99, 132, 0.5)',
          borderColor: 'rgb(0, 99, 132)',
          data: []
        }]
      };
`
  2.36: cofh.thermalexpansion.plugins.jei.JEIPluginTE;
  1.16: com.github.sokyranthedragon.mia.integrations.jer.JeiJerIntegration$1;
  1.10: jeresources.jei.JEIConfig;
  1.03: com.rwtema.extrautils2.crafting.jei.XUJEIPlugin;
  0.79: ic2.jeiIntegration.SubModule;
  0.73: crazypants.enderio.machines.integration.jei.MachinesPlugin;
  0.71: mezz.jei.plugins.vanilla.VanillaPlugin;
  0.67: knightminer.tcomplement.plugin.jei.JEIPlugin;
  0.54: com.buuz135.thaumicjei.ThaumcraftJEIPlugin;
  0.52: nc.integration.jei.NCJEI;
  0.46: com.buuz135.industrial.jei.JEICustomPlugin;
  0.38: crazypants.enderio.base.integration.jei.JeiPlugin;
  0.25: lach_01298.qmd.jei.QMDJEI;
  0.24: net.bdew.jeibees.BeesJEIPlugin;
  0.22: ninjabrain.gendustryjei.GendustryJEIPlugin;
  4.07: Other 126 Plugins
`
        .split(';')
        .map(l => l.split(':'))
        .forEach(([time, name]) => {
          a.labels.push(name);
          a.datasets[0].data.push(time)
        })
        ; return a
    })()
  }
}"/>
</p>

<br>

# FML Stuff
<p align="center">
<img src="https://quickchart.io/chart?w=500&h=400&c={
  options: {
    rotation: Math.PI,
    cutoutPercentage: 55,
    plugins: {
      legend: !1,
      outlabels: {
        stretch: 5,
        padding: 1,
        text: (v)=>v.labels
      },
      doughnutlabel: {
        labels: [
          {
            text: 'FML stuff:',
            color: 'rgba(128, 128, 128, 0.5)',
            font: {size: 18}
          },
          {
            text: [216.08,'s'].join(''),
            color: 'rgba(128, 128, 128, 1)',
            font: {size: 22}
          }
        ]
      },
    }
  },
  type: 'outlabeledPie',
  data: {...(() => {
    let a = {
      labels: [],
      datasets: [{
        backgroundColor: [],
        data: [],
        borderColor: 'rgba(22,22,22,0.3)',
        borderWidth: 2
      }]
    };
`
993A00   1.45s Loading sounds;
994400   1.52s Loading Resource - SoundHandler;
994F00  41.10s ModelLoader: blocks;
995900  14.29s ModelLoader: items;
996300   8.42s ModelLoader: baking;
996D00   1.87s Applying remove recipe actions;
997700   0.13s Applying remove furnace recipe actions;
998200   0.58s Indexing ingredients;
998C00   8.47s Indexing ingredients;
444444 138.26s Other
`
    .split(';')
      .map(l => l.match(/(\w{6}) *(\d*\.\d*)s (.*)/))
      .forEach(([, col, time, name]) => {
        a.labels.push([name, ' ', time, 's'].join(''));
        a.datasets[0].data.push(parseFloat(time));
        a.datasets[0].backgroundColor.push([String.fromCharCode(35), col].join(''))
      })
      ; return a
  })()}
}"/>
</p>

<br>
