# CloudWatchLogsAgentDemo

## はじめに

- Regionは `us-east-1` を利用（DefaultのAMIがus-east-1）
- デプロイ後は、SSMセッションマネージャからログイン可能（Outputsの `SessionManagerUrl`）
- ログはOutputsの `CloudWatchLogsUrl` から確認
  - デフォルトなので、出力ログは `/var/log/message` になります。

## 設定

- /etc/awslogs/awslogs.conf

## デプロイ

**Parameters**

|Neme|Type|Default|Description|
|--|--|--|--|
|ImageId|AWS::EC2::Image::Id|ami-0323c3dd2da7fb37d|AmazonマシンイメージID|
|InstanceType|String|t2.micro|インスタンスタイプ|

```sh
aws cloudformation create-stack \
    --region us-east-1 \
    --stack-name cloudwatch-logs-agent-demo \
    --capabilities CAPABILITY_IAM \
    --template-body file://template.yaml
```
