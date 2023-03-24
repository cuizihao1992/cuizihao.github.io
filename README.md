# cuizihao.github.io

```
<!DOCTYPE html>
<html lang="en">

<head>
  <!-- Use correct character set. -->
  <meta charset="utf-8" />
  <!-- Tell IE to use the latest, best version. -->
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <!-- Make the application on mobile take up the full browser screen and disable user scaling. -->
  <meta name="viewport"
    content="width=device-width, initial-scale=1, maximum-scale=1, minimum-scale=1, user-scalable=no" />
  <title>Hello World!</title>
  <script src="../Build/CesiumUnminified/Cesium.js"></script>
  <script>
    var scope;
    if (typeof window !== 'undefined') {
      scope = window;
      scope.Freedo = Cesium;
    } else if (typeof self !== 'undefined') {
      scope = self;
      scope.Freedo = Cesium;
    } else if (typeof module !== 'undefined') {
      scope = module;
      scope.exports = Cesium;
      scope.Freedo = module.exports;
    } else {
      scope = {};
      scope.Freedo = Cesium;
      console.log('Unable to load Cesium.');
    }
    if (typeof scope.Freedo.defineProperties === 'undefined') {
      scope.Freedo.defineProperties = Object.defineProperties;
    }
    if (typeof scope.Freedo.isArray === 'undefined') {
      scope.Freedo.isArray = Array.isArray;
    }
  </script>
  <script src="/extends/FreedoX.js"></script>
  <script src="./adjust3dTiles.js"></script>
  <script src="./test.js"></script>
  <!-- <script src="./Counter.js"></script> -->
  <script type="module">
    import { Counter } from './Counter.js'
    window.counter = Counter;
  </script>
  <style>
    @import url(../Build/Cesium/Widgets/widgets.css);

    html,
    body,
    #cesiumContainer {
      width: 100%;
      height: 100%;
      margin: 0;
      padding: 0;
      overflow: hidden;
    }
  </style>
</head>

<body>
  <div id="cesiumContainer"></div>
  <script>
    Cesium.Ion.defaultAccessToken =
      'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiIxY2Y3NzY4OC0xMjExLTRiZjUtYTU5Ny1jYzg4ZmUzNzhhZjciLCJpZCI6MjI3NjcsInNjb3BlcyI6WyJhc3IiLCJnYyJdLCJpYXQiOjE1ODIwMTQ3MTF9.7nQHPXIiwHNXpRd_cuK_TL8P-27wUKfMt2yvsiWkpyg'
    Cesium.Timeline.prototype.makeLabel = function (e) {
      let date = new Date();
      let h = 0 - date.getTimezoneOffset();
      //由于Cesium都是以JulianDate作为默认日期，所以参数e肯定为JulianDate类型，所以我们可以像上面clock改造一样改造
      let dateZone = Cesium.JulianDate.addMinutes(e, h, new Cesium.JulianDate());
      let t = Cesium.JulianDate.toGregorianDate(dateZone);
      //这里就是设置格式的地方
      //t.year + "-" + t.month + "-" + t.day
      return "asdf&nbsp;&nbsp;" + t.hour + ":" + t.minute + ":" + t.second + "&nbsp;&nbsp;";
    };
    const viewer = new Cesium.Viewer("cesiumContainer", {
      // terrainProvider: Cesium.createWorldTerrain(),
    });
    let p;
    p = viewer.entities.add(new Cesium.Entity({
      position: new Cesium.Cartesian3.fromDegrees(112.94275912383577, 22.347486012469894),//
      point: {
        color: Cesium.Color.RED,
        pixelSize: 10
      }
    })
    )

    setTimeout(() => {

      viewer.zoomTo(p)
    })
    // const imageryLayers = viewer.imageryLayers;
    // const url = 'http://10.3.4.112/cim/geoserver/gwc/service/wmts?tilematrix=EPSG:4326:14&layer=cim:cim_road_group&style=&tilerow=6140&tilecol=26764&tilematrixset=EPSG:4326&format=image/png&service=WMTS&version=1.0.0&request=GetTile';
    // let _matrixIds = ["EPSG:4326:0", "EPSG:4326:1", "EPSG:4326:2", "EPSG:4326:3", "EPSG:4326:4", "EPSG:4326:5", "EPSG:4326:6", "EPSG:4326:7", "EPSG:4326:8", "EPSG:4326:9", "EPSG:4326:10", "EPSG:4326:11", "EPSG:4326:12", "EPSG:4326:13", "EPSG:4326:14", "EPSG:4326:15", "EPSG:4326:16", "EPSG:4326:17", "EPSG:4326:18", "EPSG:4326:19", "EPSG:4326:20", "EPSG:4326:21"];
    // const wmts = new Cesium.WebMapTileServiceImageryProvider({
    //   url:
    //     "http://10.3.4.112/cim/geoserver/gwc/service/wmts",
    //   // url: 'http://localhost:8090/geoserver/gwc/service/wmts',
    //   layer: "cim:cim_road_group",
    //   style: 'default',
    //   format: "image/png",
    //   tilematrixset: "EPSG:4326",
    //   tileMatrixSetID: "EPSG:4326",
    //   tileMatrixLabels: _matrixIds,
    //   tilingScheme: new Cesium.GeographicTilingScheme({
    //     numberOfLevelZeroTilesX: 2,
    //     numberOfLevelZeroTilesY: 1
    //   })
    // })


    // let wmts1 = new Cesium.WebMapTileServiceImageryProvider({
    //   url: `http://10.3.4.117:8600/geoserver/gwc/service/wmts`, //服务地址，如：'http://localhost:8080/geoserver/gwc/service/wmts'
    //   layer: "tgis:gis_dzzh_hptt_shm", //图层名称，如：'tasmania'
    //   style: "",
    //   format: "image/png",
    //   tilematrixset: "EPSG:4326",
    //   tileMatrixSetID: "EPSG:4326",
    //   tileMatrixLabels: _matrixIds,
    //   tilingScheme: new Cesium.GeographicTilingScheme({
    //     numberOfLevelZeroTilesX: 2,
    //     numberOfLevelZeroTilesY: 1
    //   })
    // });
    // // imageryLayers.addImageryProvider(wmts1);
    // // let imageryLayer = imageryLayers.addImageryProvider(wmts1, 3);


    // const wms2 = new Cesium.WebMapServiceImageryProvider({
    //   url:
    //     "http://10.3.4.117:8600/geoserver/ows",
    //   layers: "tgis:gis_district_sz_group_shm",
    //   parameters: {
    //     transparent: true,
    //     format: "image/png",
    //   },
    // })
    // const provider = new Cesium.WebMapTileServiceImageryProvider({
    //   url:
    //     "https://basemap.nationalmap.gov/arcgis/rest/services/USGSShadedReliefOnly/MapServer/WMTS",
    //   layer: "USGSShadedReliefOnly",
    //   style: "default",
    //   format: "image/jpeg",
    //   tileMatrixSetID: "default028mm",
    //   maximumLevel: 19,
    //   credit: "U. S. Geological Survey",
    // })
    // // imageryLayers.addImageryProvider(
    // //   new Cesium.WebMapServiceImageryProvider({
    // //     url:
    // //       "https://nationalmap.gov.au/proxy/http://geoserver.nationalmap.nicta.com.au/geotopo_250k/ows",
    // //     layers: "Hydrography:bores",
    // //     layers: "Habitation:buildingareas",
    // //     parameters: {
    // //       transparent: true,
    // //       format: "image/png",
    // //     },
    // //   })
    // // );

    // //     viewer.terrainProvider = new Cesium.CesiumTerrainProvider({
    // //     url: "http://10.223.178.107/api/t-gis/gw/COMMON/dem/dem30/"
    // // })
    // // viewer.scene.globe.depthTestAgainstTerrain = true
    // const bing = new Cesium.BingMapsImageryProvider({
    //   url: 'https://dev.virtualearth.net',
    //   key: 'get-yours-at-https://www.bingmapsportal.com/',
    //   mapStyle: Cesium.BingMapsStyle.AERIAL
    // });
    // var imageryProvider = new Cesium.MapboxStyleImageryProvider({
    //   url: 'https://api.mapbox.com/styles/v1',
    //   username: 'wangfen12383', //wangfen
    //   accessToken: 'pk.eyJ1Ijoid2FuZ2ZlbjEyMzgzIiwiYSI6ImNrZGZtd2xnbzFqaWIydXBlMDJ2eTFoaTEifQ.Y-NUKtxcPcfwTjBkzBxlrg',
    //   styleId: 'ckyntl17v04no15qr5ilfpn4h',
    //   scaleFactor: true
    // })
    // viewer.imageryLayers.addImageryProvider(imageryProvider)

    var tilesetUrl = 'http://localhost:81/Data/%E5%A4%A7%E5%9D%AA%E5%B1%B1%E9%9A%A7%E9%81%93/3dtiles/tileset.json';
    tilesetUrl = 'http://localhost:81/BaiduNetdiskDownload/qjr_osgb/Production_osgb/output/tileset.json'
    tilesetUrl = 'http://localhost:81/Data/望海路FBX_83048/FBX/3dtiles2/tileset.json'
    tilesetUrl = 'http://localhost:81/Data/望海路FBX_83048/FBX/batch3dtiles/tileset.json'
    tilesetUrl = 'http://localhost:81/Data/塘朗山隧道/tileset/tileset.json'
    tilesetUrl = 'http://localhost:81/Data/塘朗山隧道/3dtiles/tileset.json'

    tilesetUrl = 'http://localhost:10010/3D Tiles/北环上步立交/tileset.json'
    tilesetUrl = 'http://localhost:10010/3D Tiles/硕果丰塑胶五金公司对侧边坡/tileset.json';//0
    tilesetUrl = 'http://localhost:10010/3D Tiles/爱国路高架桥/tileset.json';

    // tilesetUrl = 'http://localhost:10010/3D Tiles/沙井大桥/tileset.json';
    // tilesetUrl = 'http://localhost:10010/3D Tiles/梧桐山道立交梧桐山大路西/tileset.json';
    // tilesetUrl = 'http://localhost:10010/3D Tiles/彩田路北延段新彩隧道南洞口边坡/tileset.json'
    // tilesetUrl = 'http://localhost:10010/3D Tiles/龙景立交D匝道-/tileset.json'
    // var tileset0 = viewer.scene.primitives.add(new Cesium.Cesium3DTileset({
    //   url: tilesetUrl,
    // }))

    tilesetUrl = 'http://localhost:10011/一体化项目模型原文件/3dtiles/1/tileset.json';
    tilesetUrl = 'http://localhost:10011/一体化项目模型原文件/3dtiles/2/tileset.json';
    tilesetUrl = 'http://10.126.1.226:20019/bim/3dtiles/tanglangshan/tileset.json';
    tilesetUrl = 'http://localhost:10011/tanglangshanCurve/tileset.json';
    tilesetUrl = 'http://localhost:10011/北环上步立交/tileset.json';
    tilesetUrl = 'http://localhost:10011/沙井西大桥/tileset.json';
    tilesetUrl = 'http://localhost:10011/沙井大桥clm2/tileset.json';
    tilesetUrl = 'http://10.126.1.226:20018/bim/3dtiles/BIM_440300BBAM11199_shajing/tileset.json'
    let list = [
      '一体化项目-桥梁-北环上步立交-20220424',
      '一体化项目-边坡-梧桐山道立交梧桐山大路西-20220506',
      '一体化项目-边坡-福田区彩田路北延段新彩隧道南洞口边坡-20220509',
      '一体化项目-边坡-龙岗区南坪快速路龙景立交D匝道-20220524',
      '一体化项目-边坡五和大道ZK12+356～ZK12+472~ZK12+620~ZK12+890',
      '一体化项目-边坡大鹏新区溪坪路K0＋635- K1+035左侧边坡-1111',
      '一体化项目-边坡宝安区西宝线K89 +090K89H215左侧-1111',
      '一体化项目-边坡龙华区五和大道GK11+340~ZK11+680右侧边坡-1111',
      '塘朗山隧道',
      '沙井西大桥',
      '爱国路高架桥'
    ]
    tilesetUrl = `http://localhost:10011/${list[6]}/tileset.json`;
    tilesetUrl = `http://localhost:10010/${"tanglangshan"}/tileset.json`
    tilesetUrl = `https://3dmap.gcnao.cn/bim-api/assets/Ga1b8ce02e0374bbf81d90cea4657897d/tileset.json?token=eyJhbGciOiJIUzI1NiJ9.eyJhY2NvdW50SWQiOiIzMjFkODgzYmY4MjE0MDdjYjQ2ODA3MzQxODAwMjYzZCIsIm5hbWUiOiLov5DooYzmjIfmjKXkuK3lv4PmvJTnpLoiLCJ1c2VybmFtZSI6ImxpYW9saWFvMjAyMSIsInBob25lTnVtYmVyIjoiMTg5MTE0NzczNjkiLCJhY2NvdW50VHlwZSI6IlBFUlNPTkFMIiwidXNlcklkIjoiNmQ1YTI4MjRlZDc3NDMwNmI0ODUxMzU4NGNhNmNmYmQiLCJjb21wYW55SWQiOiI1NzQzOGQ2NDc5ZjU0ZTNkYjUzY2EwYWZjNmYxYzk2ZSIsImNvbXBhbnlOYW1lIjoi5LqR5Z-65pm65oWn5bel56iL6IKh5Lu95pyJ6ZmQ5YWs5Y-4IiwianRpLXV1aWQiOiJqdGktNTNlODJjZjAtYmZkMy00YTNlLWJiOTktOTlhODIyYjQ0NmQ2IiwiZXhwIjoxNjczOTQzMzQwfQ.JaMUMHTJi3ECTKtqpN3Wr-tyWowG7cPQgSa5QzxkFRc&companyId=1580021086899273729&t=1673319261562`
    // tilesetUrl = 'https://3dmap.gcnao.cn/bim-api/assets/Ga1b8ce02e0374bbf81d90cea4657897d/tileset.json?token=eyJhbGciOiJIUzI1NiJ9.eyJhY2NvdW50SWQiOiIzMjFkODgzYmY4MjE0MDdjYjQ2ODA3MzQxODAwMjYzZCIsIm5hbWUiOiLov5DooYzmjIfmjKXkuK3lv4PmvJTnpLoiLCJ1c2VybmFtZSI6ImxpYW9saWFvMjAyMSIsInBob25lTnVtYmVyIjoiMTg5MTE0NzczNjkiLCJhY2NvdW50VHlwZSI6IlBFUlNPTkFMIiwidXNlcklkIjoiNmQ1YTI4MjRlZDc3NDMwNmI0ODUxMzU4NGNhNmNmYmQiLCJjb21wYW55SWQiOiI1NzQzOGQ2NDc5ZjU0ZTNkYjUzY2EwYWZjNmYxYzk2ZSIsImNvbXBhbnlOYW1lIjoi5LqR5Z-65pm65oWn5bel56iL6IKh5Lu95pyJ6ZmQ5YWs5Y-4IiwianRpLXV1aWQiOiJqdGktN2Q0OTg2ZjItYjdlOS00OWU2LThkZWEtZGViMTNmYjQwZWU1IiwiZXhwIjoxNjczODU4NDI5fQ.TvHCKdiaRxO2kQ9nyCdeIXbSc9K2ZYb4WbN_wTbR43A&companyId=1580021086899273729&t=1673271221761'
    // tilesetUrl = './3dtiles/tileset.json';
    // tilesetUrl = 'http://10.3.4.117/api-server/api/v1/tiles_3d/name/gis_buildings_shm/tiles/tileset.json'
    // tilesetUrl = 'http://10.126.1.226:20019/bim/3dtiles/tanglangshan0908/tileset.json'
    // tilesetUrl = 'http://jk-gnss.sutpc.com:55889/3dtiles/2/tileset.json';
    // tilesetUrl = 'http://localhost:10011/3dtiles/2/tileset.json';
    // tilesetUrl = 'http://localhost:10011/3d tiles/tileset.json';
    // tilesetUrl = 'http://localhost:10011/asdf/tileset.json';
    // tilesetUrl = 'http://jk-gnss.sutpc.com:55889/3dtiles/1/tileset.json';
    // tilesetUrl = 'http://localhost:10012/data/tileset.json'
    tilesetUrl = 'http://10.126.1.226:20018/bim/3dtiles/BIM_440300BBAM11199_shajing/tileset.json'
    tilesetUrl = 'http://localhost:10010/tanglangshan/tileset.json'
    tilesetUrl = 'http://10.126.1.226:20020/3dtiles/BIM_440300BBAM11199_shajing/tileset.json'
    tilesetUrl = 'http://10.126.1.226:20020/3dtiles/BIM_440300BLHM11041_aiguolu/tileset.json'
    tilesetUrl = 'http://localhost:10010/爱国路高架桥/tileset.json'
    tilesetUrl = 'http://localhost:10010/一体化项目-桥梁-北环上步立交-20220424/tileset.json'
    // tilesetUrl = 'http://10.126.1.226:20020/3dtiles/BIM_440300BFTM11038_beihuanshabu/tileset.json'
    tilesetUrl = 'http://localhost:8000/road3dtiles/shenzhen/ftc/road/tileset.json'
    tilesetUrl = 'http://localhost:8000/road3dtiles/shenzhen/ftc/bus_station/tileset.json'
    tilesetUrl = 'http://localhost:8000/road3dtiles/shenzhen/ftc/biaopai/tileset.json'
    tilesetUrl = 'http://localhost:8000/road3dtiles/shenzhen/ftc/building/tileset.json'
    tilesetUrl = 'http://localhost:10010/china/tileset.json'
    var tileset = viewer.scene.primitives.add(new Cesium.Cesium3DTileset({
      url: tilesetUrl,
      shadows: 0,
      maximumScreenSpaceError: 0
    }))
    // test2();
    // const tms = new Cesium.UrlTemplateImageryProvider({
    //   url: Cesium.buildModuleUrl('Assets/Textures/NaturalEarthII') + '/{z}/{x}/{reverseY}.jpg',
    //   // url: 'http://10.10.180.64:58899/map0/service?t=blue&x={x}&y={y}&z={z}',
    //   // url: 'http://10.10.180.64:58899/map0/service?t=blue&x={x}&y={reverseY}&z={z}',
    //   url: "http://localhost:8080/proxy-t-gis/api/t-gis/gw/OGC/POI_ZFJG/?layer=GGSS%3AGGSS120_pt&style=&tilematrixset=EPSG%3A4490&Service=WMTS&Request=GetTile&Version=1.0.0&Format=image%2Fpng&TileMatrix=EPSG%3A4490%3A2&TileCol=3347&TileRow=766",
    //   url:"http://localhost:8080/proxy-t-gis/api/t-gis/gw/OGC/POI_ZFJG/?layer=GGSS:GGSS120_pt&style=&tilematrixset=EPSG:4490&Service=WMTS&Request=GetTile&Version=1.0.0&Format=image/png&TileMatrix=EPSG:4490:{z}&TileCol={x}&TileRow={y}",
    //   tilingScheme: new Cesium.GeographicTilingScheme(),
    //   // tilingScheme: new Cesium.WebMercatorTilingScheme()
    // });
    // viewer.imageryLayers.addImageryProvider(tms)
    const shadedRelief2 = new Cesium.WebMapTileServiceImageryProvider({
      url: 'http://basemap.nationalmap.gov/arcgis/rest/services/USGSShadedReliefOnly/MapServer/WMTS/tile/1.0.0/USGSShadedReliefOnly/{Style}/{TileMatrixSet}/{TileMatrix}/{TileRow}/{TileCol}.jpg',
      layer: 'USGSShadedReliefOnly',
      style: 'default',
      format: 'image/jpeg',
      tileMatrixSetID: 'default028mm',
      maximumLevel: 19,
      credit: new Cesium.Credit('U. S. Geological Survey')
    });
    // viewer.imageryLayers.addImageryProvider(shadedRelief2);
    let arcgisProvider = new Cesium.ArcGisMapServerImageryProvider({
      url:
        "https://services.arcgisonline.com/ArcGIS/rest/services/NatGeo_World_Map/MapServer/",
      url: 'http://localhost:8080/proxy-t-gis/api/t-gis/gw/ESRI/GTKJ_DY_YLWS/MapServer/',
      url: 'http://10.223.178.107/api/t-gis/gw/ESRI/SZMAP_WATER_ZW2K/MapServer/'
      // url: 'http://10.223.178.107/api/t-gis/gw/ESRI/GTKJ_DY_JY/MapServer/',
      // url:'http://10.223.178.107/api/t-gis/gw/ESRI/SZMAP_ROAD_GK2K/MapServer/',
      // layers: ['一级医院'],
      // layers: ['一级医院','二级医院','三级医院','卫生应急机构','全市医疗机构']
    })
    // viewer.imageryLayers.addImageryProvider(arcgisProvider);
    // tileset.style = new Cesium.Cesium3DTileStyle({
    //   color: {
    //     conditions: [
    //       ['(${name}==="' + '桥供南' + '")', 'color("#ff0000", 0.2)'],
    //       ['(${name}==="' + '桥供北' + '")', 'color("#ff0000", 0.2)'],
    //       ['(${name}==="' + '4号墩横梁' + '")', 'color("#ffff00", 0.7)'],
    //       ['(${name}==="' + '桥墩2型' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅1号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅2号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅3号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅6号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅7号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅8号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //       // ['(${name}==="' + '右幅9号桥墩' + '")', 'color("#0000ee", 0.7)'],
    //     ]
    //   },
    //   color: "color('rgba(255,255,255," + 0.9 + ")')",
    //   show: {
    //     conditions: [['(${name}==="' + '二次衬砌' + '")', false]]
    //   }
    // });
    viewer.zoomTo(tileset)

    var th = new FreedoX.FdMicroApp.FdTransformHelper(viewer);
    // th.setData([model]);
    // th.start("MOVE|ROTATE|SCALE");

    // adjust3dTiles
    var tilesets = [tileset]
    setTimeout(() => {
      // return
      th.setData(tilesets);
      th.start("MOVE|ROTATE|SCALE");
      th.on(function (eventType, eventArg) {
        if (eventType == "DataChanged") {
          data = th.tranOptions;
        }
        //监控这个时间可以得到模型编辑之后的最新modelMatrix
        //然后在数据加载的时候指定这个modelMatrix就可以了
        if (eventType == "TransformedMatrix") {
          //console.log(eventArg);
        }
      })
    }, 1000)
    function addModel() {
      let url = "http://localhost:81/Data/大坪山隧道/fengji.gltf"
      url = 'http://localhost:81/Code/SUTPC/frontend/public/static/tunnel/gltf/Car/Car_White.glb'
      var origin = Cesium.Cartesian3.fromDegrees(118.087308, 24.644866, 0);
      var modelMatrix = Cesium.Transforms.eastNorthUpToFixedFrame(origin);
      let options = {
        url,
        modelMatrix
      }
      model = this.model = viewer.scene.primitives.add(Cesium.Model.fromGltf(options))
      model.readyPromise.then(m => {
        var bs = model.boundingSphere;
        var newCenter = Cesium.Matrix4.multiplyByPoint(modelMatrix, bs.center, new Cesium.Cartesian3());
        var newBS = new Cesium.BoundingSphere(newCenter, bs.radius);
        model.initModelMatrix = Cesium.clone(model.modelMatrix, true);
        viewer.camera.viewBoundingSphere(newBS, new Cesium.HeadingPitchRange(0, -0.5, 0));
        viewer.camera.lookAtTransform(Cesium.Matrix4.IDENTITY);
      })
    }
    function polyline() {
      var ple = new Freedo.FdMicroApp.FdPolylineEditor(viewer);
      ple.setHeightOffset(0);
      ple.setAutoLoop(false);
      ple.start();

      ple.on(function (eventType, eventArg) {
        if (eventType == "PLAdd") {
          needSave = true;
          console.log(eventArg);
        }

        if (eventType == 'EditEnd') {
          var localData = Freedo.clone(ple.pleOptions, true);
          localData[currentIndex].pts = Freedo.clone(eventArg.pts, true);
          ple.pleOptions = localData;
        }
      })
    }
    function projectVideo() {
      var mm = new Freedo.FdModel.FdModelManager(viewer);
      var lon = 118.910267083;
      var lat = 32.117140878;

      viewer.scene.camera.flyTo({
        destination: Freedo.Cartesian3.fromDegrees(lon, lat, 100.0),
        orientation: {
          heading: Freedo.Math.toRadians(180),
          pitch: Freedo.Math.toRadians(-90.0),
          roll: 0.0
        }
      });

      var params = {
        longitude: lon,
        latitude: lat,
        altitude: 20,
        heading: 180,
        pitch: 0.0,
        roll: -90.0,
        fov: 90.0,
        ratio: 1.2,
        farClip: 20.0,
        depthBias: -0.001
      };
      options = {
        position: Freedo.Cartographic.fromDegrees(params.longitude, params.latitude, params.altitude),
        heading: params.heading,
        pitch: params.pitch,
        roll: params.roll,
        fov: params.fov,
        ratio: params.ratio,
        farClip: params.farClip,
        depthBias: params.depthBias
      }
      var video
      if (Freedo.defined(video)) {
        video.dispose();
        video = undefined;
      }
      var videoUrl = 'http://127.0.0.1:5501/JS/5.mp4'
      video = mm.add('Video', {
        url: videoUrl,
        params: options,
      });
      show = true;
    }

  </script>
</body>

</html>
```
