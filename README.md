# Next.js + Tailwind CSS + Shopify Starter

フロントエンドにNext.js + Tailwind CSSを使用し、Shopify Storefront APIを利用してShopifyバックエンドと通信します。完全に機能するオンラインストアです。実際に動作するデモは[こちら](https://doggystickers.xyz/ "Shopify store")からご覧いただけます。

GraphQLを使ってShopifyのデータを照会し、カートの情報をlocalStorageに保存してユーザーのセッションを保持します。最後に、Shopify Checkoutを使用してユーザーが商品を購入できます。

## 使用スタック

* Next.js + Tailwind CSS
* GraphQL
* ユーザーセッションを保存するlocalStorage
* Shopify
* vercel

## 使用方法

デフォルトでは、ストアは1つのコレクション内のすべての商品を照会して表示するように設定しています。複数のコレクションやストア全体を照会できます。

### GraphQL クエリでのページネーションについての注意点

すべてのGraphQL クエリは、Shopify で 250 に設定されている最大数の製品/バリエーション/画像を取得するようにハードコードしています。これは、ページネーションによりクエリを複雑にしないためです。ほとんどのユースケースで250は十分と考えられます。

もし、ページネーションが必要な場合は、[cursor](https://youtu.be/S37WsC8GzSA "graphql pagination")フィールドを追跡し、すべてのアイテムを取得するまで問い合わせします。

### 環境変数の設定

ルートディレクトリに`.env.local`ファイルを作成します。以下の4つの変数を追加する必要があります。

```
SHOPIFY_STORE_FRONT_ACCESS_TOKEN=
SHOPIFY_STORE_DOMAIN=
SHOPIFY_COLLECTION=
NEXT_PUBLIC_LOCAL_STORAGE_NAME=
```

`SHOPIFY_STORE_FRONT_ACCESS_TOKEN`と`SHOPIFY_STORE_DOMAIN`（DOMAIN_NAME.myshopify.comのようになります）は、Shopify Storefront APIのアクセスに必要です。ShopifyストアでAPIが利用できるように設定されていることを確認してください。詳しくは[docs](https://shopify.dev/docs/storefront-api/getting-started "Shopify store")をご覧ください。

`SHOPIFY_COLLECTION`は取り込みたいコレクションの名前です。`NEXT_PUBLIC_LOCAL_STORAGE_NAME`は、ユーザーがカート情報を保存するためのキーの名前です。正確な名前はそれほど重要でありませんが、ユニークな名前にすることをお勧めします。他の保存されたオブジェクトと衝突する可能性が低くなります。「yourStoreNameShopifyStore」のように、「yourStoreName」があなたのshopifyストア名であれば十分です。

### インストール

プロジェクトのディレクトリーに移動し、以下のコマンドを実行します。

```
yarn && yarn dev
```

### サイトのメタデータの更新

サイトのメタデータは、next.config.jsファイルで更新できます。

```
env: {
  siteTitle: 'あなたの会社',
  siteDescription: 'あなたの会社の説明です',
  siteKeywords:'あなたの会社のキーワード',
  siteUrl: 'https://doggystickers.xyz',
  siteImagePreviewUrl: '/images/main.jpg',
  twitterHandle: '@your_handle'
}
```

### 色の更新

カラーパレットの更新はtailwind.config.jsファイルで行います。

```
colors: {
  palette: {
    lighter: '',
    light: '',
    primary: '',
    dark: '',
  },
},
```

### プログレッシブ・ウェブ・アプリ（PWA）データの更新

`manifest.json`ファイルと、`public/images/icons`ディレクトリー配下のアイコンを更新します。
https://realfavicongenerator.net/ などのオンラインの無料ツールを使用すると、すべての異なるアイコンサイズと favicon.ico ファイルをすばやく生成できます。

## デプロイ

様々なサービスを使ってデプロイできます。本サイトでは、Vercel をしています。セットアップや Github リポジトリーとの同期が非常に簡単です。


## ライセンス

オリジナルのコードと同様にMTIライセンスを採用しています。

https://github.com/GraphCMS/graphcms-commerce-starter

## 注意事項

コード自体のローカライズはWIPです。また、準備でき次第公開して参ります。
