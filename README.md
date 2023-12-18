# eco-map

環境センサーデータビジュアライズ

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

## 統計 250m メッシュの表示

### 市区町村別メッシュ・コード一覧

500m メッシュまでかな、市区別にメッシュ ID が参照できる
https://www.stat.go.jp/data/mesh/m_itiran.html

### 都道府県別 250m メッシュ

GeoJSON が入手できる(CSV もある)
サンプルとして神奈川県のメッシュデータを入れてある
`/data/14kanagawa250m.geojson`
https://www.geospatial.jp/ckan/dataset/npli-pref-250m

### サンプルデーター

GeoJSON に埋め込んでしまったが、ほんとは外に出すべき。

```
{
    "type":"Feature",
    "properties":{
        "code": "5339153512",
        "PM2.5": 2.18, // ←ここに独自プロパティを足している
        "CO2": 874, // ←ここに独自プロパティを足している
        "VOC": 93 // ←ここに独自プロパティを足している
    },
    "geometry":{
        "type":"Polygon",
        "coordinates":[
            [
                [139.690625,35.4416666666667],
                [139.69375,35.4416666666667],
                [139.69375,35.44375],
                [139.690625,35.44375],
                [139.690625,35.4416666666667]
            ]
        ]
    }
},
```

### 今後の展開

- 環境センシングデータ（ポイント）をメッシュ単位で集計処理しておく機能が必要
  - 各値ごとに平均値を出して、メッシュ ID にまとめておくような処理
- メッシュの色塗り分けロジック
  - 各メッシュが持っているプロパティの値を見て分岐させる
  - 加重平均できるとか、閾値を設定できるとか、汎用的に使えるロジックを実装しておく

### 参考

https://note.com/ryoearth/n/n779386780fbb
