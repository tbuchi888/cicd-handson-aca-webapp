# TASK05: Azure WebApp for containers でのコンテンツの手動デプロイを体感
<img width="801" alt="image" src="assets/c7982159-8b58-49bb-980c-cee90acb9070.png">
<BR>
<BR>

* Azure WebApp for containers を利用して、コンテナによるコンテンツの手動デプロイをしていきます。
  * コンテナは、TASK02で作成したイメージを利用します。

## 1. 事前準備 Azure WebApp for containers の作成
<img width="263" alt="image" src="assets/69e7af6d-092c-49f8-994e-e3de759a345e.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0c433caf-f5ae-4483-8ddc-f8eacbb39038.png">
<BR>
<BR>

クイックスタートを利用してAzure Appサービスプラン 環境および　Azure WebApp for containers（Webアプリ）　を新規に作成します。

`基本`タブ
* サブスクリプション: 今回のHandsOnで利用可能なサブスクリプション
* リソースグループ： handsonRG-NN（同一 Azure　サブスクリプション内でユニークなRG名、NNはチーム独自の数字など）
* インスタンスの詳細
  * 名前: webapphandsonNNNNNNNN(任意の文字列ですが、本 Azure サービス内でユニークである必要あり)
  * 公開: Docker コンテナー
  * オペレーティング システム: Linux
  	Windows
  * 地域: Japan East
* 価格プラン
  * Linux プラン（Japan East）: 新規作成
  * 価格ブラン：　Basic B1
* 上記以外デフォルト値
 
> [!WARNING]
> * サブスクリプションについて、必ず今回のHandsOn用のものであることを確認してください。
> * 商用環境で利用しているサブスクリプションへ誤ってデプロイしないように注意してください。
> * また、複数チームで同一のサブスクリプションを利用している場合、リソースグループの後に参加チーム独自の数字をつけるなどして、重複しないようユニークとなるようにしてください。

<BR>
<BR>
<img width="801" alt="image" src="assets/959acbd4-c51e-4817-b404-b09d7de7359a.png">
<BR>
<BR>

`データベース`、`Docker`、`ネットワーク`、`監視`、`タグ`、`確認と作成`タブ
* 全てデフォルト値
  
<BR>
<BR>
<img width="801" alt="imageDb" src="assets/0030623d-5c90-40d7-8b8f-ffdc68a78989.png">
<BR>
<BR>
 
<img width="801" alt="imageDocker" src="assets/626eaec4-1659-4f59-bd6a-63e1c0f99332.png">
<BR>
<BR>

<img width="801" alt="imageNetwork" src="assets/3f36c71f-d805-4148-b778-3c3049bec624.png">
<BR>
<BR>

<img width="801" alt="imageInsight" src="assets/b2baf090-1781-4598-9ed3-032774dc823b.png">
<BR>
<BR>

<img width="801" alt="imageTag" src="assets/5cc0faf6-8b5b-4101-af7e-5234340a8311.png">
<BR>
<BR>

<img width="801" alt="imageCreate" src="assets/22dbfae1-12d3-40da-8310-e0fecc0d0cdb.png">
<BR>
<BR>

作成をクリック

<BR>
<BR>
<img width="801" alt="imageCreate" src="assets/77f90f14-abef-4124-9b40-1c86d88c7457.png">
<BR>
<BR>
<img width="801" alt="imageCreate" src="assets/11098999-f274-47e6-97d3-664aa91fe23f.png">
<BR>
<BR>

デプロイが完了したら`リソースに移動`をクリックし作成した`Webapp`の概要画面を表示

<BR>
<BR>
<img width="801" alt="imageCreate" src="assets/11098999-f274-47e6-97d3-664aa91fe23f.png">
<BR>
<BR>


つづいて`既定のドメイン`をクリックし、クイックスタートの画面が表示されることを確認

<BR>
<BR>
<img width="801" alt="imageCreate" src="assets/c1e83bd3-5416-49b5-a211-989b594e4798.png">
<BR>
<BR>

## 2. Azure WebApp for containers への手動デプロイ
<img width="801" alt="image" src="assets/c7982159-8b58-49bb-980c-cee90acb9070.png">
<BR>
<BR>

前 Task にて作成したコンテナイメージをデプロイします。左メニューより、[デプロイメント]-[`デプロイ センター`]をクリックし

<BR>
<BR>
<img width="801" alt="image" src="assets/6bffd144-f28c-49ab-860c-22c328b216a6.png">
<BR>
<BR>

* レジストリの設定
  *　レジストリ ソース：　dockerhub 
  * 完全なイメージの名前とタグ: `[REPLACE-YOUR-DOCKER-ID]`/nginx-js:v1
* 上記以外デフォルト値
  
<BR>
<BR>
<img width="801" alt="imageCreate" src="assets/85773a58-0262-4328-94c0-e40b090088b2.png">
<BR>
<BR>

画面上部の`保存`をクリックし設定を反映

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`は必ず、自身の Docker ID に置き換えてください！

`概要`メニューに戻り

<BR>
<BR>
<img width="801" alt="image" src="assets/11098999-f274-47e6-97d3-664aa91fe23f.png">
<BR>
<BR>

`既定のドメイン`をクリック
TASK02で作成したコンテナイメージがデプロイされていることを確認（変更されない場合、ブラウザの更新をクリック）

<BR>
<BR>
<img width="801" alt="imagev1" src="assets/8b5d2651-d0e3-462f-aceb-9d739adacc7e.png">
<BR>
<BR>

左メニューより、[デプロイメント]-[`デプロイ センター`]に戻り、

* レジストリの設定
  *　レジストリ ソース：　dockerhub 
  * 完全なイメージの名前とタグ: `[REPLACE-YOUR-DOCKER-ID]`/nginx-js:v2
* 上記以外デフォルト値

画面上部の`保存`をクリックし設定を反映

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`は必ず、自身の Docker ID に置き換えてください！

<BR>
<BR>
<img width="801" alt="image" src="assets/90d68e15-73ff-4749-a44d-37be4f139701.png">
<BR>
<BR>

`概要`メニューに戻り

<BR>
<BR>
<img width="801" alt="image" src="assets/11098999-f274-47e6-97d3-664aa91fe23f.png">
<BR>
<BR>

`既定のドメイン`をクリック
TASK02で作成した v2 コンテナイメージがデプロイされていることを確認します。（変更されない場合、ブラウザの更新をクリック）

<BR>
<BR>
<img width="801" alt="imagev2" src="assets/ScreenShot 2023-12-08 16.18.38.png">
<BR>
<BR>


以上でこちらのタスクは完了です。

---

## アジェンダ
+ [TASK0: 事前準備](README.md#task0-%E4%BA%8B%E5%89%8D%E6%BA%96%E5%82%99)
+ [TASK1: docker build 用 VM を作成](01-create-a-vm-for-docker-build.md)
+ [TASK2: VM でのコンテンツの手動デプロイを体感](02-vm-manual-deploy.md)
+ [TASK3: Azure Container Apps でのコンテンツの手動デプロイを体感](03-containerapps-manual-deploy.md)
+ [TASK4: Azure Container Apps での CI/CD を体感](04-containerapps-cicd.md)
+ [TASK5: Azure WebApp for containers でのコンテンツの手動デプロイを体感](05-webapp-manual-deploy.md)
+ [TASK6: Azure WebApp for containers での CI/CD を体感](06-webapp-cicd.md)
