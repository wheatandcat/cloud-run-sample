---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Cloud Runの紹介
# persist drawings in exports and build
drawings:
  persist: false
title: Cloud Runの紹介
layout: intro
colorSchema: 'light'
---

# Cloud Runの紹介

<div class="flex justify-center">
  <img
    class="w-80 pt-2"
    src="/logo.png"
  />
</div>

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

<div class="flex pb-5">
  <div class="px-5">
    <div class="rounded-full bg-white w-30 h-30 overflow-hidden border-2 border-black border-dotted border-opacity-20">
      <img
        class="w-40 pt-2"
        src="/account.png"
      />
    </div>
  </div>
  <div class="mt-11">
    <h2><b>自己紹介</b></h2>
  </div>
</div>
<br />
<br/>

- 📝 飯野陽平（[wheatandcat](https://github.com/wheatandcat)）
- 🏢 フリーランスエンジニア（シェアフル株式会社CTO）
- 💻 Blog: https://www.wheatandcat.me/
- 🛠 今までに作ったもの
  - [memoir](https://memoir-lp-mvbeacmwe-wheatandcat.vercel.app/)
  - [ペペロミア](https://peperomia.app/)
  - [Atomic Design Check List](https://atomic-design-checklist.vercel.app/)


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  color: #696969;
  @apply font-500;
  font-size:1.15rem;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **Cloud Run**とは

<br/>

 - Cloud Run は、スケーラブルなインフラストラクチャ上でコンテナを直接実行できるマネージド コンピューティング プラットフォーム。
 - コンテナ イメージをビルドしてデプロイして使用できる。
 - 構成、スケーリングは設定で即座に変更可能。

<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1.25rem;
}
</style>

---

# **実行形式**
<br/>
Cloud Runには以下の2つの実行形式がある
<br/>
<br/>


### **Cloud Run Service**
 - 主な用途: APIサーバー、webサイト、イベント処理
 - できること
  - 自動スケーリング、各種スケーリングの設定

<br/>

### **Cloud Run Jobs**
 - 主な用途: バッチ処理、ツール
 - Cloud Run Serviceとの差は以下の通り
   - 設定タイムアウトの時間を最大1時間まで設定可能
   - 最大再試行回数を設定できる
   - 並列処理


<style>

</style>

---

# **Cloud Run**の使い方

<br/>

Cloud Runでは以下の2つの方法でコンテナイメージの作成が可能。

 - **Dockerfile** を使用する
 - **Buildpacks** を使用する

<br/>

---

# **Buildpacks**とは

<br/>

Buildpacksは、ソースコードから読み取りベストプラクティスに則ってDockerfileを書かずにイメージを生成してくれるツールで、現状だと以下のプラットフォームで対応している。

 - Go
 - Node.js
 - Python
 - Java
 - .NET Core


<br/>

[Learn More](https://buildpacks.io)


<style>
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  @apply font-500;
  font-size:1.25rem;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>


---

# **Cloud Run Service**をデプロイしてみる①

<br/>

以下のチュートリアルをベースに、デプロイを紹介 

- [Cloud Run に Go サービスをデプロイする](https://cloud.google.com/run/docs/quickstarts/build-and-deploy/deploy-go-service)


<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **Cloud Run Service**をデプロイしてみる②

<br/>

以下のコマンドでイメージを作成

```bash
$ gcloud builds submit --pack image=IMAGE_URL
```

上記で、GCPの**Artifact Registry**にイメージが作成されるので、以下のコマンドでCloud Runにデプロイ


```bash
$ gcloud run deploy $SERVICE_NAME \
          --project=$PROJECT_ID \
          --image=$IMAGE_URL \
          --region=$REGION
```

[Learn More](https://cloud.google.com/artifact-registry?hl=ja)

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **環境変数**の設定
<br/>

<div>環境変数の設定はコンソールから設定可能</div>

 - [環境変数の設定](https://cloud.google.com/anthos/run/docs/configuring/environment-variables?hl=ja)


<br/>
<div class="flex">
  <img
    class="w-100 pt-2"
    src="/item_001.png"
  />
</div>

<br/>
<br/>

<div>環境変数で機密情報を設定する場合は<b>Secret Manager</b>の値をマウントできる。</div>

 - [シークレットを使用する](https://cloud.google.com/run/docs/configuring/secrets?hl=ja)


<br/>

<style>
a {
  color: #84b9cb;
  @apply font-500;
}
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
ul {
  padding-left: 1rem;
  margin-top: 0.1rem;
}
li {
  color: #696969;
  @apply font-500;
  font-size:1.1rem;
}
</style>

---

# 継続的デプロイの方法
<br/>

GitHub Actionsを使用して実装したので紹介

<br/>

■ <b>Cloud Runへ移行</b><br/>
- https://github.com/wheatandcat/memoir-backend/pull/117/files

<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **Cloud Run Jobs**を試してみる①
<br/>

以下のチュートリアルをベースに紹介 

- [Cloud Run で Go ジョブをビルドして作成する](https://cloud.google.com/run/docs/quickstarts/jobs/build-create-go?hl=ja)


<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **Cloud Run Jobs**を試してみる②

<br/>

以下のコマンドでイメージをデプロイ

```bash
$ gcloud builds submit --pack image=gcr.io/PROJECT_ID/logger-job
```

以下のコマンドで作成したコンテナを使用してジョブを作成する

```bash
$ gcloud beta run jobs create $JOB_NAME \
    --image gcr.io/PROJECT_ID/logger-job \
    --tasks 50 \
    --set-env-vars SLEEP_MS=10000 \
    --set-env-vars FAIL_RATE=0.5 \
    --max-retries 5 \
    --region REGION
```

以下のコマンドで実行

```bash
$ gcloud beta run jobs execute $JOB_NAME
```

<style>
span {
  font-size:0.5rem;
  line-height: 1.2em;
}
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# **Cloud Run Jobs**を試してみる③

<br/>

結果は、コンソールで確認できる

<div class="flex">
  <img
    class="w-100 pt-2"
    src="/item_002.png"
  />
</div>

---

# 並列実行


<br/>

以下の記事を元に紹介

- [Cloud Run jobs を解説する](https://medium.com/google-cloud-jp/cloud-run-jobs-c963a7143367)

<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>
---

# **Cloud Scheduler**にJobを設定する

<br/>

以下のチュートリアルをベースに紹介 

- [スケジュールに従ってジョブを実行する](https://cloud.google.com/run/docs/execute/jobs-on-schedule?hl=ja#console)

<br/>

URLには以下を設定する

```
https://REGION-run.googleapis.com/apis/run.googleapis.com/v1/namespaces/PROJECT-ID/jobs/JOB-NAME:run
```

<style>
a {
  color: #84b9cb;
  @apply font-500;
}
</style>

---

# まとめ

<br/>

 - GCPの推しているサービスなだけあってスキの無い作りだった
 - **Cloud Run Jobs**の登場でバッチ処理もカバーできるようになった
 - **Cloud Run Jobs**は、まだ**プレビュー**の状態なので注意


<style>
a {
  color: #84b9cb;
  @apply font-500;
}
p {
  line-height: 1.6em;
}
</style>

---
layout: center
class: "text-center"
---

<div class="text-2xl font-700 text-enter w-full">
  <div>ご清聴ありがとうございました</div>
</div>


<style>
.main {
  display: flex;
  height: 80%;
  width: 100%;
  justify-content: center;
  align-items: center;
  color: #46AE35;
}
</style>


