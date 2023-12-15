# TASK06： Azure WebApp for containers での CI/CD を体感
<img width="801" alt="image" src="assets/a9afbe6c-8f60-44e2-9347-9d952ce174bc.png">
<BR>
<BR>
Azure WebApp for containers と Github リポジトリを連携し、Github Actions により コンテナイメージのビルド（CI）と Azure WebApp for containers へのデプロイをしていきます。

## 1. 事前準備 Github リポジトリの作成
<img width="500" alt="image" src="assets/741a0fab-152c-425c-8247-f2ed086cb01e.png">
<BR>
<BR>
Azure WebApp for containers の CI/CD に利用する Github リポジトリの作成します。

[https://github.com/](https://github.com/) へログインします。
画面右上メニューの`＋`より`Import repository`を選択してクリックします。

<BR>
<BR>
<img width="801" alt="ScreenShot 2023-11-30 17 31 04" src="assets/df32e87a-87b2-4f88-ba0d-e63fec934718.png">
<BR>
<BR>

以下を入力して`Begin import`をクリックします。

* Your old repository’s clone URL: [https://github.com/tbuchi888/demo-handson-aca-cicd.git](https://github.com/tbuchi888/demo-handson-webapp-cicd.git)
* Repository Name: handson-webapp-cicd
* Privacy: Private（任意 Publicでも可）
* Importing complete! Your new repository [YOUR-GITHUB-ACCOUNT-NAME]/handson-webapp-cicd is ready.と表示されるまでまって 表示されている作成されたリポジトリへのリンクをクリックします。

<BR>
<BR>
<img width="801" alt="image" src="assets/efffd4b3-7522-44d7-a91e-ffee2d0e81d1.png">
<BR>
<BR>
<img width="801" alt="image" src="assets/848e23c8-f4bc-47a7-b56d-96a632ddb00e.png">
<BR>
<BR>
<img width="801" alt="image" src="assets/6950720f-6358-4714-a7af-aa854a29561f.png">
<BR>
<BR>

つづいて、右上メニュー`Settings`をクリックし、左メニューの[General][Code and automation][Actions][General]より
Actions permissions　の設定を　`Allow all actions and reusable workflows`へ変更し`Save`をクリックし、Github Actions の実行をこのリポジトリで許可します。

<BR>
<BR>
<img width="801" alt="image" src="assets/001e7c54-fb7c-431d-b13b-5526baa70497.png">
<BR>
<BR>

## 2. Azure WebApp for containers での継続的デプロイ（CI/CD）の設定
<img width="801" alt="image" src="assets/20b94498-efbb-4045-a533-e8dd3c2ca498.png">
<BR>
<BR>
Azure Portal より、TASK05 で作成した Azure WebApp for containers と Github レポジトリ、Docker hub を連携するCI/CDを設定します。

<BR>
<BR>

> [!TIP]
> GitHub Actions を使用した Azure WebApp for containers へのデプロイについて、手動で設定を行う場合、
> [https://learn.microsoft.com/ja-jp/azure/app-service/app-service-sql-asp-github-actions](https://learn.microsoft.com/ja-jp/azure/app-service/app-service-sql-asp-github-actions)を参考に、
> `Service Principal` の作成や、GitHub Actions 側でパスワード等`Secret`等の設定、ワークフローの作成が必要となりますが、
> 今回は、Azure WebApp for containers　で用意されている`デプロイセンターの`機能により、自動的にワークフローの設定を行います。

<BR>
<BR>
Azure WebApp の左メニューより、[デプロイメント]-[`デプロイ センター`]をクリックし`ソース：　Github Actions`　を選択します。

<BR>
<BR>
<img width="801" alt="image" src="assets/7312b5c7-7d09-4e9d-97e3-c7ce42075643.png">
<BR>
<BR>

`アプリに対して基本認証が無効になっています。有効にするには、こちらをクリックして構成設定に移動してください。`メッセージが表示されるためクリックをして設定を変更します。

<BR>
<BR>
<img width="801" alt="image" src="assets/cf866e0f-c786-42cd-b2f7-6fabfb923f55.png">
<BR>
<BR>

`全般設定`タブをクリックし、以下設定を変更して、画面上部メニューの`保存`をクリック

* プラットフォームの設定
  * 基本認証の発行資格情報: オン（オフからオンへ変更）

<BR>
<BR>
<img width="801" alt="image" src="assets/501a3e52-410e-4149-85ae-e801c0ca4355.png">
<BR>
<BR>
<img width="801" alt="image" src="assets/f2143e2f-db12-4415-b69c-5982cdc75831.png">
<BR>
<BR>

`続行`をクリックして変更を反映させます。

<BR>
<BR>
<img width="801" alt="image" src="assets/83d58181-ba34-4aa8-8499-a2cddaa9606e.png">

右上の`X`をクリックし、`デプロイ センター`へ戻ります。

<BR>
<BR>
<img width="801" alt="image" src="assets/316c8512-ce0e-433b-bd6b-2635712b475e.png">
<BR>
<BR>

以下設定値に変更して、画面上部の`保存`をクリックし設定を反映

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`、 [REPLACE-YOUR-DOCKER-PASSWORD]は必ず、自身の Docker ID、パスワード に置き換えてください！

* GitHub　Actions
  * 次のユーザーとしてサインイン： さきほどインポートした　HandsOn用のものと同じGithubアカウントと連携し（Authorize Azure App Service Authentication）、Azureからのリポジトリからのアクセスを許可
  * 組織: さきほどインポートした　HandsOn用のものと同じ組織
  * リポジトリ：　handson-webapp-cicd さきほどインポートした　HandsOn用のものを選択
  * ブランチ：　main
* レジストリの設定
  * リポジトリ ソース: Docker　Hub
  * ログイン: [REPLACE-YOUR-DOCKER-ID]
  * パスワード: [REPLACE-YOUR-DOCKER-PASSWORD]
  * イメージ名：　nginx-js (TASK03 で利用したものと同じイメージ名でアカウント名やタグは含めないことに注意)
* 上記以外デフォルト値

デプロイセンターイの設定が以下のように正常に完了することを確認

<BR>
<BR>
<img width="801" alt="image" src="assets/caba1222-625a-4736-8ccb-c12962bea3a6.png">
<BR>
<BR>

つづいて、Github リポジトリにもどり、CI/CDのワークフロー（`.github/workflows`）が新規追加されていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/12740d40-c1a3-4c86-a490-68df7e5e18cf.png">
<BR>
<BR>

ワークフローの中身も確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/16ebc21e-5df5-4131-ba2a-7fd4b096d57b.png">
<BR>
<BR>

Github の上部メニュー[Actions]をクリックし新規に追加された CI/CD のワークフローが起動し、正常に終了（グリーンのチェックマーク）していることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/e7924207-dd04-44c6-b8da-e7aa50ff2a1f.png">
<BR>
<BR>

つづいて、ワークフローのリンクをクリックし、さらに`build`および`deploy`をそれぞれクリックし中身を確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/3c0f82d5-f55a-4c16-b959-45b33bb64441.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0d07f1b8-8393-4edb-ae7d-445f43a677d7.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/8d9f0399-fd67-4ab6-927a-ef45e46d80e3.png">
<BR>
<BR>

## 3. Azure WebApp for containers での継続的デプロイ（CI/CD）の実行
<img width="801" alt="ScreenShot" src="assets/ffcd2844-f2a1-425d-8159-b74646b1adc4.png">
<BR>
<BR>

Azure WebApp for containers　での継続的デプロイ（CI/CD）の準備が整いましたので、
Github上のコンテンツの変更　Push　をトリガーに、Github Actions のワークフローが自動で起動し、以下 CI/CD が実行されることを確認していきます。
* CI： コンテナイメージの Build　と　docker hub へイメージが Push される
* CD： Azure WebApp for containersへ、CI でビルドされたコンテナイメージとタグ名に変更された、新規コンテンツがデプロイされる

Github 上のコンテンツの変更するために、[YOUR-GITHUB-ACCOUNT-NAME]/handson-aca-cicdのリポジトリを以下いずれかの方法で開きます。
* PC　上へをクローン（git clone）し、VSCODE　等で編集
* または　　Github Codespaces で編集
* または 推奨しませんが、Github Portal から直接コードを編集
  
以下は Github Codespaces での例

以下のファイルについて変更を行い（git commit）、 main ブランチへ　git push します。
* `html/index.html`
  * v1 を v2 に全て変更する
* `html/css/style.css`
  * 88行目の`background-color: #c9f2ff;`を任意の色（HEX値）に変更する、たとえば`#38b48b`

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/d96d14f2-f947-4acc-be79-d968a68fdce5.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/1bcb33d3-f7cf-4919-bb8a-4351d19fc8e4.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/a2941202-52f2-4824-8fe5-66f2b2fdb1e8.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/e6b5fa45-3f3e-4b9e-b712-167e50547d5d.png">
<BR>
<BR>

変更の Commit を main ブランチ への Push をトリガーにワークフローが自動起動することを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0d18200d-f813-4a20-a990-af9bedb04082.png">
<BR>
<BR>

main ブランチ へ変更内容を確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/92cc369f-365e-4b3d-8f7d-7a9a08bbb70a.png">
<BR>
<BR>

[Actions]メニューより、ワークフローが自動起動されていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0d06b1ba-5edf-49bc-8871-4dfb99e206cf.png">
<BR>
<BR>

ワークフローをクリックし、`build`および`deploy`のジョブの中で、変更されたコンテンツにより、コンテナイメージがビルドされる

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/4bc8d9cd-1fb4-4a71-b5d0-019ca02dada3.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/3d20c870-bfc1-4980-96c4-4df6d7ba25e1.png">
<BR>
<BR>

ワークフローの正常終了を確認した後に、まず Docker hub のリポジトリへ、ビルドされたコンテナイメージが追加されていることを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/65ed0d22-007d-4511-a020-9f9973e1e605.png">
<BR>
<BR>

つづいて、ブラウザより、Azure WebApp for containers　の`既定のドメイン`へアクセスし、コンテンツが変更されていることを確認します。

> [!TIP]
> ブラウザの更新をしても背景色が変更されない場合は、プライベートウィンドウでご確認ください

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/37dc677c-d721-4646-9e4a-ff1b841376bd.png">
<BR>
<BR>

Webapp の`概要`へ戻り、コンテナが、GitHub コミット ID (SHA) を使用してタグ付けされていることを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/bf3dfced-653e-48c2-b80c-0174ec31c5d4.png">
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
