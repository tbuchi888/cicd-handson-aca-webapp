# cicd-handson-aca-webapp
こちらは、Github Actions のサンプルを利用した CIOps CI/CD Handson の手順を説明したものとなります。
+ 記載の内容については、2023年11月21日時点の環境（ OSS や、その他 Azure 等プラットフォームのバージョン）をベースとしています。
+ **なお、こちらに記載の内容はあくまでサンプルとなりますので、ご注意ください。**
<img width="801" alt="image" src="./assets/17949085/0ccd7a92-3225-405c-92d3-dd19843b6ec0.png">

## TASK0: 事前準備
本 Handson では、開始前に以下の準備ができていることを前提としています。
参加チーム毎に事前準備をお願いします

+ Hands on 用 Azure Subscription 準備
  + 用途： アプリデプロイ用のAKS(Azure Kubernetes Service)及び、AKS上でGitOpsのOSSツール（ArgoCD）を動作させます
  + 参考： [Azure の無料アカウント](https://azure.microsoft.com/ja-jp/free/)より新規作成
+ Github アカウントの準備
  + アカウントが存在しない場合： [Github Top ページの Sign up for GitHub](https://github.com/) より新規作成
  + 用途：GitOps用のプロジェクト並びに、CI用のプロジェクトを作成します
+ dockerhub Account 準備
  + アカウントが存在しない場合： [Dockerhub Top ページの Get Started Today for Free](https://hub.docker.com/) より新規作成
  + 用途：CIで作成するコンテナイメージ（Publicを想定）を格納します
    
---
## アジェンダ
+ [TASK0: 事前準備](README.md#task0-%E4%BA%8B%E5%89%8D%E6%BA%96%E5%82%99)
+ [TASK1: docker build 用 VM を作成](01-create-a-vm-for-docker-build.md)
+ [TASK2: VM でのコンテンツの手動デプロイを体感](02-vm-manual-deploy.md)
+ [TASK3: Azure WebApp for containers でのコンテンツの手動デプロイを体感](03-containerapps-manual-deploy.md)
+ [TASK4: Azure WebApp for containers での CI/CD を体感](04-containerapps-cicd.md)
+ [TASK5: Azure WebApp for containers でのコンテンツの手動デプロイを体感](05-webapp-manual-deploy.md)
+ [TASK6: Azure WebApp for containers での CI/CD を体感](06-webapp-cicd.md)
