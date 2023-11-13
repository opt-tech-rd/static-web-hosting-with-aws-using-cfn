# CloudFormationによる静的WEBホスティング環境構築サンプル

AWSの提供するIaCである [CloudFormation](https://aws.amazon.com/jp/cloudformation/)を使って、CloudFront + ACM + S3による静的WEBホスティング環境を構築するサンプルコードです。  

## 前提

実行にあたり以下の前提条件があります。  
- 実行ユーザにPowerUser程度のIAMポリシーが付与されていること
- 構築済みのRoute53ホストゾーンが存在すること

## 実行

1. [ホストゾーン一覧](https://us-east-1.console.aws.amazon.com/route53/v2/hostedzones)から自身のホストゾーンIDを控える  
1. WEB環境のドメインを決める  
1. 本リポジトリをクローンする  
    ```
    git clone git@github.com:opt-tech-rd/static-web-hosting-with-aws-using-cfn.git
    ```
1. [CloudFormationスタック作成](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create)のテンプレートファイルのアップロードより本リポジトリの `template.yaml`をアップロード  
    リージョンが `バージニア北部` であることを確認すること  
1. 以下のパラメータを入力し、作成する  
    - スタック名(任意)
    - DefaltRootObject(ルートURLにアクセスした際開くファイル。通常はデフォルトのindex.html)
    - DomainName(WEB環境のドメイン名を入力)
    - HostedZoneId(自身の所持するRoute53ホストゾーンのホストゾーンIDを入力)
