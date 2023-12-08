# TASK07: Option
時間に余裕がある場合は、以下にもチャレンジしてみてください。

## Option1: Dockerhub から Azure Container Registry
* 難易度：　**
* Azure Container Registry を新規に作成し、Dockerhub と置き換えてみましょう。
  * 詳細手順はこちらでは、載せませんので[公式ドキュメント](https://learn.microsoft.com/ja-jp/azure/container-registry/)等を参考に実施してみてください。

## Option2: AKS GitOps
* 難易度：　***
* AKS を利用した GitOps HandsOn
  * [https://github.com/tbuchi888/cicd-handson](https://github.com/tbuchi888/cicd-handson)
 
## Option3: Azure Conitainer Appでのカナリアリリース * Github Action
* 難易度：　*******
* Azure Conitainer App にて、複数のリビジョンを利用したカナリアリリース（新規割合を10％等）を実現してみましょう。
  * 手動でのオペレーションの確認
    * 　以下参考 
      * Azure Conitainer App のリビジョンモードを`複数`にする
      * リビジョンを追加し、トラフィックを変更する
      * 使用しない古いリビジョンを非アクティブにする
  * AZ CLI等 を利用した新規リビジョンの作成手順の確立
  * Github Actions の作成
    
> [!TIP]
> * [Azure Container Apps の変更を更新してデプロイする](https://learn.microsoft.com/ja-jp/azure/container-apps/revisions)
> * [Azure Container Apps でのトラフィック分割](https://learn.microsoft.com/ja-jp/azure/container-apps/traffic-splitting?pivots=azure-cli)
> * [Azure コンテナー アプリでの Blue-Green デプロイ](https://learn.microsoft.com/ja-jp/azure/container-apps/blue-green-deployment?pivots=azure-cli)
> * [Azure Container Apps でリビジョンを管理する](https://learn.microsoft.com/ja-jp/azure/container-apps/revisions-manage?tabs=bash)
>   * [https://learn.microsoft.com/ja-jp/azure/container-apps/revisions#revision-modes](https://learn.microsoft.com/ja-jp/azure/container-apps/revisions#revision-modes) 
> * [Azure Container Apps で Azure CLI を使用して GitHub Actions を設定する](https://learn.microsoft.com/ja-jp/azure/container-apps/github-actions-cli?tabs=bash)
> * [Github Actions 環境変数](https://docs.github.com/ja/actions/learn-github-actions/variables#default-environment-variables)
> * [Github Actions Setting an environment variable](https://docs.github.com/en/actions/using-workflows/workflow-commands-for-github-actions#setting-an-environment-variable)
> * [https://github.com/Azure-Samples/containerapps-blue-green](https://github.com/Azure-Samples/containerapps-blue-green)
