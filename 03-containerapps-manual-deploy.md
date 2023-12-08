# TASK03: Azure Container Apps でのコンテンツの手動デプロイを体感
<img width="801" alt="ScreenShot" src="assets/42766132-ebe0-4cea-a243-94d8fd5f832f.png">
<BR>
<BR>

* Azure Container Apps を利用して、コンテナによるコンテンツの手動デプロイをしていきます。
  * コンテナは、TASK02で作成したイメージを利用します。

## 1. 事前準備 Azure Container Apps の作成
<img width="500" alt="ScreenShot" src="assets/cf1868e2-a94d-446e-9fd9-e373bba99ce3.png">
<BR>
<BR>

クイックスタートを利用してAzure Container Apps環境およびAzure Container Appsを新規に作成します。

`基本`タブ
* サブスクリプション: 今回のHandsOnで利用可能なサブスクリプション
* リソースグループ： handsonRG-NN（同一 Azure　サブスクリプション内でユニークなRG名、NNはチーム独自の数字など）
* コンテナー アプリ名：acahandsonNNNNNNNN(任意の文字列ですが、本 Azure サービス内でユニークである必要あり)
* Container Apps 環境
  * 地域: Japan East
  * Container Apps 環境: 新規作成
* 上記以外デフォルト値
 
> [!WARNING]
> * サブスクリプションについて、必ず今回のHandsOn用のものであることを確認してください。
> * 商用環境で利用しているサブスクリプションへ誤ってデプロイしないように注意してください。
> * また、複数チームで同一のサブスクリプションを利用している場合、リソースグループの後に参加チーム独自の数字をつけるなどして、重複しないようユニークとなるようにしてください。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/b31491a9-de45-4e66-94a8-92c2587fb989.png">
<BR>
<BR>

Container Apps環境の新規作成をクリック
`基本`タブ
* 環境名: acae-handson
* 上記以外デフォルト値
  
`ワークロードプロファイル`、`監視`、`ネットワーク`タブ
* 全てデフォルト値

<img width="801" alt="ScreenShot" src="assets/3e327159-387d-4b56-be43-9a0371287078.png">
<BR>
<BR>

<img width="801" alt="ScreenShot" src="assets/63701b5e-b7ad-41a6-94a8-350b2ddd6660.png">
<BR>
<BR>

<img width="801" alt="ScreenShot" src="assets/841a4167-390f-4bd9-8880-66848ed09065.png">
<BR>
<BR>

<img width="801" alt="ScreenShot" src="assets/007b5de6-835d-4300-93b6-7c991e991fa4.png">
<BR>
<BR>

作成をクリックし、 Container Apps　に戻り

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/b31491a9-de45-4e66-94a8-92c2587fb989.png">
<BR>
<BR>

`コンテナー`、`Bindings`、`タグ`、`確認と作成`タブ
* 全てデフォルト値
  
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/c01ac780-a162-4087-85be-bc58108ad719.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/a2328569-c9cd-4f6f-8552-6a10b2f2a4cd.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/a0729795-99b7-489a-9476-2a8484f6bdda.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0284239c-646f-4963-ae70-21edfdea6e3b.png">
<BR>
<BR>

作成をクリック

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/853bc5eb-77d8-461f-bd9c-f2f18bc6fdf3.png">
<BR>
<BR>

デプロイが完了したら`リソースに移動`をクリックし作成した`Container Apps`の概要画面を表示

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/3e943e1e-36ca-4a4b-adc5-dc7740485d0b.png">
<BR>
<BR>

つづいて`アプリケーション URL`をクリックし、クイックスタートの画面が表示されることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/90330968-d3e2-453a-b63e-1c81a788cfd2.png">
<BR>
<BR>

## 2. Azure Container Apps への手動デプロイ
<img width="801" alt="ScreenShot" src="assets/42766132-ebe0-4cea-a243-94d8fd5f832f.png">
<BR>
<BR>

前 Task にて作成したコンテナイメージをデプロイします。左メニューより、[アプリケーション]-[`リビジョン`]をクリックし

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/f575925e-3879-41ef-962b-31e10ca61336.png">
<BR>
<BR>

続いて、上部の`新しいリビジョンを作成`
`コンテナー`タブ
* リビジョンの詳細
  * 名前/サフィックス: nginx-js-1
  * その他： デフォルト値
* コンテナー イメージ

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/d014ab8e-2f17-4cde-ba70-89e3567a4b7e.png">
<BR>
<BR>

元からある、クイックスタートのコンテナ`simple-hello-world-container`を選択（チェックボックス）して、`削除`をクリック

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/7b5071e4-1837-466d-be7e-de97371003f6.png">
<BR>
<BR>

`+ 追加`をクリックし、`アプリコンテナー`をクリック
`基本`タブ
* コンテナーの詳細
  * 名前：　nginx-js
  * イメージのソース：　Docker Hubまたはその他のレジストリ
  * イメージとタグ: `[REPLACE-YOUR-DOCKER-ID]`/nginx-js:v1
* コンテナー リソースの割り当て
  * CPU コア：　0.25
  * メモリ (Gi): 0.5
* 上記以外デフォルト値

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`は必ず、自身の Docker ID に置き換えてください！

`追加`をクリック

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/aeb92d47-00b5-4d02-96a4-8b22eacc21be.png">
<BR>
<BR>

`作成`をクリック

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/85bcf172-17bf-4551-8898-ac688584479f.png">
<BR>
<BR>

新規にリビジョンが作成されトラフィックが100、さらに古いリビジョンのトラフィックが0になっていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/ec4c1c85-5b7e-4253-bd38-824f396a7b83.png">
<BR>
<BR>

画面上部の`最新の情報に更新`をクリック
古いリビジョンが、アクティブなリビジョンから消えていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/22c4a99e-8bfe-4471-8c7c-9499a0cae9bd.png">
<BR>
<BR>

`概要`メニューに戻り

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/3e943e1e-36ca-4a4b-adc5-dc7740485d0b.png">
<BR>
<BR>

`アプリケーション URL`をクリック
TASK02で作成したコンテナイメージがデプロイされていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/8b5d2651-d0e3-462f-aceb-9d739adacc7e.png">
<BR>
<BR>

左メニューより、[アプリケーション]-[`リビジョン`]に戻り、

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/cc544592-35c2-4a44-83de-03c384e4f0d4.png">
<BR>
<BR>

続いて、上部の`新しいリビジョンを作成`
`コンテナー`タブ
* リビジョンの詳細
  * 名前/サフィックス: nginx-js-2
  * その他： デフォルト値
* コンテナー イメージ
  * `nginx-js`をクリック

`コンテナーの編集`
* コンテナーの詳細
  * イメージとタグ: `[REPLACE-YOUR-DOCKER-ID]`/nginx-js:v2

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`は必ず、自身の Docker ID に置き換えてください！

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0793848f-aa99-4b81-b042-77989d33bce5.png">
<BR>
<BR>

上記以外そのままで`保存`をクリック

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/514ddc3d-6df0-47ff-9d5c-4cde32f49aa5.png">
<BR>
<BR>

コンテナー イメージのタグが`v2`になっていることを確認して`作成`をクリック

あたらしい`リビジョン`としてデプロイされていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/4c9778ab-eb3c-4d02-ae21-34bfc8a4e8e1.png">
<BR>
<BR>

`概要`メニューに戻り
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/4c9778ab-eb3c-4d02-ae21-34bfc8a4e8e1.png">
<BR>
<BR>

`アプリケーション URL`をクリック
TASK02で作成した v2 コンテナイメージがデプロイされていることを確認します。
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/70cfcf9c-e1fa-4874-9bae-ecc31e834834.png">
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
