---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: JavaScript API
description: Geolonia の JavaScript API の概要を説明いたします。

micro_nav: true

# Page navigation
# page_nav:
#     prev:
#       content: JavaScript API
#       url: /js/
#     next:
#       content: クラスリファレンス
#       url: '/js/class/'

breadcrumbs:
    - title: JavaScript API
      url: /javascript-api/
---

## Geolonia の JavaScript API について

Geolonia の JavaScript API は、[Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/) の拡張クラスで、同じオプションやプロパティ、メソッド等が使用できます。

また、[Embed API](/embed-api/) によって、緯度や経度などのオプションを HTML の `data-*` 属性を使用して設定することができ、少ない記述で地図アプリケーションの開発を始めることができます。

**HTML**

```html
<div
  id="map"
  data-lat="35.6759"
  data-lng="139.7449"
  data-zoom="14"
></div>
```

**JavaScript**

```javascript
const map = new geolonia.Map('#map')
```

<a class="codepen" href="https://codepen.io/geolonia/pen/xxGWwrN" target="codepen"><i class="icon icon--codepen"></i> CodePen でサンプルコードを編集</a>

## Mapbox GL JS との互換性

Geolonia の JavaScript API は、[Mapbox GL JS](https://docs.mapbox.com/mapbox-gl-js/) を内部で使用しており、Mapbox GL JS のクラス名 `mapboxgl` を `geolonia` に置き換えるだけで、すべてのほぼすべてのクラスおよびそのインスタンスメンバー、イベントを利用できます。

Mapbox GL jS:

```javascript
const map = new mapboxgl.Map( '#map' )
```

Geolonia:

```javascript
const map = new geolonia.Map( '#map' )
```

`Map()` 以外のクラスも同様に `geolonia` に置き換えてご利用ください。 (例: `geolonia.Popup()` など)

<div class="callout callout--danger">
  <ul>
    <li>Mapbox と Geolonia の地図では API キーの受け渡しに関する仕様が違うため、API キーに関わる部分だけ互換性がありません。</li>
    <li>また、ベクトルタイルのスキーマが違うため、スタイル用の JSON については仕様は同じですが流用はできません。</li>
  </ul>
</div>

### プロパティ、メソッドおよびイベントについて

上述しましたが、クラス `mapboxgl` と `geolonia` は互換性があります。

`geolonia` に含まれる各クラスのインスタンスメンバーや、イベントについては、Mapbox GL JS のドキュメントを御覧ください。

[https://docs.mapbox.com/mapbox-gl-js/api/](https://docs.mapbox.com/mapbox-gl-js/api/)

以下は、`moveend` イベントで、地図の中心点の座標をコンソールに出力するサンプルです。

```javascript
const map = new geolonia.Map({
  container: '#map',
  maxZoom: 16,
  minZoom: 10,
})

map.on('moveend', () => {
  console.log(map.getCenter().toArray())
})
```

<a class="codepen" href="https://codepen.io/geolonia/pen/ZEGxQbd" target="codepen"><i class="icon icon--codepen"></i> CodePen でサンプルコードを編集</a>

## サンプルアプリケーション

### 地図を回転させる

以下の例では、地図のロードが完了したあとで、3秒毎に地図を反時計回りに回転させます。

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="geolonia" data-slug-hash="poJLoBq" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Rotate the Map">
  <span>See the Pen <a href="https://codepen.io/geolonia/pen/poJLoBq">
  Rotate the Map</a> by Geolonia (<a href="https://codepen.io/geolonia">@geolonia</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

<a class="codepen" href="https://codepen.io/geolonia/pen/poJLoBq" target="codepen"><i class="icon icon--codepen"></i> CodePen でサンプルコードを編集</a>

### 複数のマーカーを表示

この例では、GeoJSON を読み込んで、条件ごとに色分けしたマーカーを表示しています。

<p class="codepen" data-height="265" data-theme-id="dark" data-default-tab="result" data-user="geolonia" data-slug-hash="zYGRgdq" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Multiple Markers with GeoJSON">
  <span>See the Pen <a href="https://codepen.io/geolonia/pen/zYGRgdq">
  Multiple Markers with GeoJSON</a> by Geolonia (<a href="https://codepen.io/geolonia">@geolonia</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

<a class="codepen" href="https://codepen.io/geolonia/pen/zYGRgdq" target="codepen"><i class="icon icon--codepen"></i> CodePen でサンプルコードを編集</a>