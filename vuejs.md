# Vue.js

[環境構築](./vue/settings.md)
[import文](./vue/import.md)
[vueファイル](./vue/vuefile.md)

### 単一コンポーネントとVite

コンポーネントとはただのファイル。そのファイルの拡張子は.vue。このファイルのことを単一ファイルコンポーネントという。

## 初期設定

```
npm create vue@latest
```

上記のコマンドで色々設定を聞かれる
例）
Project name: vue-lesson
Add TypeScript?
...

#### create-vueで作成したファイルがどうなっているのか

- vite.config.js：Viteの設定ファイル
- READ.md
- package.json：
-- scripts：コマンドと関係している
-- dependencies：プロジェクトに必要なパッケージ、本番環境
-- devDependencies：プロジェクトに必要なパッケージ、開発環境
- 

```
npm install
```
dependencies、devDependenciesにそってnode-moduleがインストールされる

```
npm run dev
```
開発用のサーバ立ち上げ

```
npm run build
```
開発がすべて終わってリリースするときにはじめてつかう。distフォルダを作成してくれる。
```
npm run preview
```
distフォルダをプレビューする。本番環境
```
npm run list
```
コードが正しくかけているかチェックしてくれる
```
npm run format
```
コードをキレイにフォーマットしてくれる

## createApp
```
createApp
```
引数に指定されたコンポーネントをもとにしてユーザーインターフェースを作る。

