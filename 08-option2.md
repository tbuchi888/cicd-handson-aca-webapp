# TASK08: Option2
時間に余裕がある場合は、以下にもチャレンジしてみてください。

## Option4: Azure Conitainer Appでのカナリアリリース * Github Action
* 難易度：　**********
* 回答例は用意しておりません。
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
