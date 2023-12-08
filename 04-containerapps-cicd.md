# TASK04： Azure Container Apps での CI/CD を体感
<img width="801" alt="ScreenShot" src="assets/ffcd2844-f2a1-425d-8159-b74646b1adc4.png">
<BR>
<BR>

Azure Container Apps と Github リポジトリを連携し、Github Actions により コンテナイメージのビルド（CI）と　Azure Container Apps　へのデプロイをしていきます。

## 1. 事前準備 Github リポジトリの作成
<img width="801" alt="ScreenShot" src="assets/741a0fab-152c-425c-8247-f2ed086cb01e.png">
<BR>
<BR>

Azure Container Apps の CI/CD に利用する Github リポジトリの作成します。

[https://github.com/](https://github.com/) へログインします。
画面右上メニューの`＋`より`Import repository`を選択してクリックします。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/df32e87a-87b2-4f88-ba0d-e63fec934718.png">
<BR>
<BR>

以下を入力して`Begin import`をクリックします。

* Your old repository’s clone URL: https://github.com/tbuchi888/demo-handson-aca-cicd.git
* Repository Name: handson-aca-cicd
* Privacy: Private（任意 Publicでも可）
* Importing complete! Your new repository [YOUR-GITHUB-ACCOUNT-NAME]/handson-aca-cicd is ready.と表示されるまでまって 表示されている作成されたリポジトリへのリンクをクリックします。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/2aeec6b5-efc0-4612-a5ac-32372ca71a8a.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/c62d7def-cb71-47ab-a875-1437fde9d1a0.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/2c0f6f49-33b8-48b3-8dac-d5ff9c26677a.png">
<BR>
<BR>

つづいて、右上メニュー`Settings`をクリックし、左メニューの[General][Code and automation][Actions][General]より
Actions permissions　の設定を　`Allow all actions and reusable workflows`へ変更し`Save`をクリックし、Github Actions の実行をこのリポジトリで許可します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/352952c6-a6c4-43fd-9da6-9b274b5c8364.png">
<BR>
<BR>


## 2. Azure Container Apps での継続的デプロイ（CI/CD）の設定
<img width="801" alt="ScreenShot" src="assets/f6f08785-70e7-4004-8acb-3a9a8aeb831e.png">
<BR>
<BR>

Azure Portal より、TASK03 で作成した Azure Container Apps と Github レポジトリ、Docker hub を連携するCI/CDを設定します。
> [!TIP]
> GitHub Actions を使用した Azure Container Apps へのデプロイについて、手動で設定を行う場合、
> [https://learn.microsoft.com/ja-jp/azure/container-apps/github-actions](https://learn.microsoft.com/ja-jp/azure/container-apps/github-actions)を参考に、
> `Service Principal` の作成や、GitHub Actions 側でパスワード等`Secret`等の設定、ワークフローの作成が必要となりますが、
> 今回は、Azure Container Apps　で用意されている`継続的デプロイ`機能により、自動的にワークフローの設定を行います。

Azure Container Apps の左メニュー[設定][継続的デプロイ]を開き以下を設定し`継続的デプロイの開始`をクリックします。

> [!CAUTION]
> 以下`[REPLACE-YOUR-DOCKER-ID]`、 [REPLACE-YOUR-DOCKER-PASSWORD]は必ず、自身の Docker ID、パスワード に置き換えてください！

* GitHub 設定
  * サインイン： さきほどインポートした　HandsOn用のものと同じGithubアカウントと連携し（Authorize Azure App Service Authentication）、Azureからのリポジトリからのアクセスを許可
  * 組織: さきほどインポートした　HandsOn用のものと同じ組織
  * リポジトリ：　handson-aca-cicd さきほどインポートした　HandsOn用のものを選択
  * ブランチ：　main
* レジストリの設定
  * リポジトリ ソース: Docker hub またはその他のレジストリ
  * イメージ：　nginx-js (TASK03 で利用したものと同じイメージ名でアカウント名やタグは含めないことに注意)
  * ログイン サーバー URL: docker.io
  * ユーザー名: [REPLACE-YOUR-DOCKER-ID]
  * パスワード: [REPLACE-YOUR-DOCKER-PASSWORD]
* サービス プリンシパルの設定
 * サービス プリンシパル：　新規作成
* 上記以外デフォルト値
   
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/f1a53079-351e-48b9-9f81-be4da025f415.png">
<BR>
<BR>

Authorize Azure App Service Authentication　のポップアップ画面

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/11b2c12c-5a27-4495-9de4-9b813c92d16a.png">
<BR>
<BR>

継続的デプロイの設定が以下のように正常に完了することを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/9fefff79-a09d-4593-acca-94e233b43170.png">
<BR>
<BR>

つづいて、Github リポジトリにもどり、CI/CDのワークフロー（`.github/workflows`）が新規追加されていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/2f6602f8-b36a-4b8b-b0b0-fb4fced00bf4.png">
<BR>
<BR>

ワークフローの中身も確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/d3c8a876-3341-4b2d-815e-8e2d2c267da3.png">
<BR>
<BR>

Github の上部メニュー[Actions]をクリックし新規に追加された CI/CD のワークフローが起動し、正常に終了（グリーンのチェックマーク）していることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0aea5349-bc01-46e3-804a-f91bd30d9968.png">
<BR>
<BR>

つづいて、ワークフローのリンクをクリックし、さらに`build-and-deploy`をクリックし中身を確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/674d02ac-38e1-4eb1-b52a-b3668e29e611.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/8d03a6bd-ddf2-425e-8d3e-4f72132ed296.png">
<BR>
<BR>

## 3. Azure Container Apps での継続的デプロイ（CI/CD）の実行
<img width="801" alt="ScreenShot" src="assets/ffcd2844-f2a1-425d-8159-b74646b1adc4.png">
<BR>
<BR>

Azure Container Apps　での継続的デプロイ（CI/CD）の準備が整いましたので、
Github上のコンテンツの変更　Push　をトリガーに、Github Actions のワークフローが自動で起動し、以下 CI/CD が実行されることを確認していきます。
* CI： コンテナイメージの Build　と　docker hub へイメージが Push される
* CD： Azure Container Apps上のリビジョンについて、CI でビルドされたコンテナイメージとタグ名に変更され、新規コンテンツがデプロイされる

Github 上のコンテンツの変更するために、[YOUR-GITHUB-ACCOUNT-NAME]/handson-aca-cicdのリポジトリを以下いずれかの方法で開きます。
* PC　上へをクローン（git clone）し、VSCODE　等で編集
* または　　Github Codespaces で編集
* または 推奨しませんが、Github Portal から直接コードを編集
  
以下は Github Codespaces での例

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/a27d20e4-2e49-47de-92a2-a1eb245354ac.png">
<BR>
<BR>

以下のファイルについて変更を行い（git commit）、 main ブランチへ　git push します。
* `ｈｔｍｌ／index.html`
  * v1 を v2 に全て変更する
* `html/css/style.css`
  * 88行目の`background-color: #c9f2ff;`を任意の色（HEX値）に変更する、たとえば`#ffdbed`

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/ea298da3-5804-4a93-bfdf-b51e2f5c461b.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/bb9a7ebf-71de-4c97-bb4b-203cfb241dfa.png">
<BR>
<BR>

変更の Commit を main ブランチ への Push をトリガーにワークフローが自動起動することを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/881d47b2-6529-4d8e-92f2-fe5be2d9297c.png">
<BR>
<BR>

main ブランチ へ変更内容を確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/68d3e408-9c0d-4bb6-8478-f8d6f853eb1f.png">
<BR>
<BR>

[Actions]メニューより、ワークフローが自動起動されていることを確認

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/691b3f6d-e65b-4be6-a75d-988282df534c.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/02a8d5f5-0c6e-4e5f-adb8-a838225290ca.png">
<BR>
<BR>

`build-and-deploy`のジョブの中で、変更されたコンテンツにより、コンテナイメージがビルドされる

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/60d167ea-d072-477d-b11c-49c2f177fba2.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/0ee4edc1-9d28-4338-91a2-9dc710e30a33.png">
<BR>
<BR>

ワークフローの正常終了を確認した後に、まず Docker hub のリポジトリへ、ビルドされたコンテナイメージが追加されていることを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/e8e37233-5f89-4cf5-9bf0-023eecf79e09.png">
<BR>
<BR>


つづいて、ブラウザより、Azure Container Apps　のコンテンツが変更されていることを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/8c2a54d0-8813-47a4-bbfc-2379ad86a098.png">
<BR>
<BR>

また、Azure Container Apps　側では新規のリビジョンが追加されていること

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/d61f6dcf-fa73-4a66-823d-ee653701bdaa.png">
<BR>
<BR>

コンテナが、GitHub コミット ID (SHA) を使用してタグ付けされていることを確認します。

<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/6d411e20-9c63-4c92-8f25-070d336e4c0d.png">
<BR>
<BR>
<img width="801" alt="ScreenShot" src="assets/99afd471-6e19-4b50-a8bf-04d4b6595c80.png">
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
