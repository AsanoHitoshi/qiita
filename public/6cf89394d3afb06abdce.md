---
title: 【Rails】google mapを表示させよう
tags:
  - HTML
  - JavaScript
  - Rails
  - GoogleMapsAPI
private: false
updated_at: '2019-09-20T14:26:20+09:00'
id: 6cf89394d3afb06abdce
organization_url_name: null
slide: false
ignorePublish: false
---
#概要
今回はGoogleMapを任意のビューに表示させる方法について解説します
#準備
ビューファイルとgoogle mapのAPIキーを準備しましょう
##APIキー
公式サイト（https://console.developers.google.com/?hl=ja ）から手順に沿ってAPIキーを取得しましょう
今回は省略します
#ビュー

```html:
<div id="map" style="width: 500px;height: 350px;"></div>

<script>
      var map;
      function initMap() {
        map = new google.maps.Map(document.getElementById('map'), {
          center: {lat: -34.397, lng: 150.644},
          zoom: 8
        });
      }
</script>

<script src="https://maps.googleapis.com/maps/api/js?key=APIキー&callback=initMap"
    async defer></script>
```

解説、始めます！！！

`var map;`
まず、マップの変数を定義します
`new google.maps.Map(document.getElementById('map')`
そしてマップをビューのidがmapの要素に生成します
`center: {lat: -34.397, lng: 150.644},`表示させるマップの中心を設定します
`zoom: 8`マップの倍率を設定します
公式ドキュメントによると
1: World
5: Landmass/continent
10: City
15: Streets
20: Buildings
が基準のようです
参考に設定してみてください

最後に
`APIキー`の部分に個人で取得したAPIキーを代入してください！！

これで表示が完璧です！！

他にもピン留め、ピンからウィンドウを表示させたり、地名や建物名から検索もできます！！
色々やってみましょう！！
###質問、気になるところなどございましたらコメントよろしくお願いします
