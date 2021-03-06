---
aliases:
  - /ja/serverless/troubleshooting/installing_the_forwarder/
dependencies:
  - 'https://github.com/DataDog/datadog-serverless-functions/blob/master/aws/logs_monitoring/README.md'
kind: ドキュメント
title: Datadog Forwarder
---
Datadog Forwarder は、ログ、カスタムメトリクス、トレースを環境から Datadog に送信する AWS Lambda 関数です。Forwarder は次のことができます。

- CloudWatch、ELB、S3、CloudTrail、VPC、CloudFront ログを Datadog に転送する
- S3 イベントを Datadog に転送する
- Kinesis データストリームイベントを Datadog に転送する (CloudWatch ログのみがサポートされています)
- CloudWatch ログを使用して AWS Lambda 関数からカスタムメトリクスを転送する
- CloudWatch ログを使用して AWS Lambda 関数からトレースを転送する
- AWS REPORT ログから解析された拡張 Lambda メトリクス (`aws.lambda.enhanced.*`) を生成して送信する: duration、billed_duration、max_memory_used、timeouts、out_of_memory、and estimated_cost

## インストール

Datadog は、[CloudFormation](#cloudformation) を使用して Forwarder を自動的にインストールすることをお勧めします。[Terraform](#terraform) を使用するか、[手動](#manually)でセットアッププロセスを完了することもできます。

<!-- xxx tabs xxx -->
<!-- xxx tab "Cloud Formation" xxx -->

### CloudFormation

[![Launch Stack](https://s3.amazonaws.com/cloudformation-examples/cloudformation-launch-stack.png)](https://console.aws.amazon.com/cloudformation/home#/stacks/create/review?stackName=datadog-forwarder&templateURL=https://datadog-cloudformation-template.s3.amazonaws.com/aws/forwarder/latest.yaml)

1. 管理者 AWS アカウント/ロールにログインし、上のボタンで CloudFormation Stack をデプロイします。
2. `DdApiKey` を入力し、適切な `DdSite` を選択します。他のすべてのパラメーターはオプションです。
3. **Create stack** をクリックし、作成が完了するまで待ちます。
4. スタックの "Resources" タブで、論理 ID が `Forwarder` のインストール済みの Forwarder Lambda 関数を見つけます。
5. インストールされた Forwarder へのトリガーを[自動](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#automatically-setup-triggers)または[手動](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#manually-setup-triggers)で設定します。
6. 複数の AWS リージョンで運用している場合は、別のリージョンで上記の手順を繰り返します。

<!-- xxz tab xxx -->
<!-- xxx tab "Terraform" xxx -->

### Terraform

Terraform リソース [aws_cloudformation_stack](https://www.terraform.io/docs/providers/aws/r/cloudformation_stack.html) を、指定されている CloudFormation テンプレートのラッパーとして使用して、Forwarder をインストールします。

Datadog は、2 つの個別の Terraform コンフィギュレーションを作成することをお勧めします。

- 最初のものを使用して Datasecret API キーを AWS Secrets Manager に保存し、出力から適用するシークレット ARN を書き留めます。
- 次に、Forwarder の別のコンフィギュレーションを作成し、`DdApiKeySecretArn` パラメーターを介してシークレット ARN を指定します。

API キーと Forwarder のコンフィギュレーションを分離すると、Forwarder を更新するときに Datadog API キーを指定する必要がなくなります。

**注:** CloudFormation テンプレートには `DdApiKey` パラメーターが必要であるため、適用するプレースホルダー値 (任意の値) を指定する必要があります。将来的に Forwarder を更新またはアップグレードするには、Forwarder コンフィギュレーションを再度適用します。

#### コンフィギュレーション例

```tf
# AWS Secrets Manager に Datadog API キーを保存します
variable "dd_api_key" {
  type        = string
  description = "Datadog API key"
}

resource "aws_secretsmanager_secret" "dd_api_key" {
  name        = "datadog_api_key"
  description = "Encrypted Datadog API Key"
}

resource "aws_secretsmanager_secret_version" "dd_api_key" {
  secret_id     = aws_secretsmanager_secret.dd_api_key.id
  secret_string = var.dd_api_key
}

output "dd_api_key" {
  value = aws_secretsmanager_secret.dd_api_key.arn
}
```

```tf
# S3 と CloudWatch からのログ、および Lambda 関数からの可観測性データを Datadog へ送信する Datadog Forwarder。
# https://github.com/DataDog/datadog-serverless-functions/tree/master/aws/logs_monitoring
resource "aws_cloudformation_stack" "datadog_forwarder" {
  name         = "datadog-forwarder"
  capabilities = ["CAPABILITY_IAM", "CAPABILITY_NAMED_IAM", "CAPABILITY_AUTO_EXPAND"]
  parameters   = {
    DdApiKey           = "this_value_is_not_used"
    DdApiKeySecretArn  = "REPLACE ME WITH THE SECRETS ARN"
    FunctionName       = "datadog-forwarder"
  }
  template_url = "https://datadog-cloudformation-template.s3.amazonaws.com/aws/forwarder/latest.yaml"
}
```

<!-- xxz tab xxx -->
<!-- xxx tab "手動" xxx -->

### 手動

指定されている CloudFormation テンプレートを使用して Forwarder をインストールできない場合は、以下の手順に従って Forwarder を手動でインストールできます。テンプレートの機能について改善できる点がございましたら、お気軽に問題やプルリクエストを開いてお知らせください。

1. 最新の[リリース](https://github.com/DataDog/datadog-serverless-functions/releases)から、`aws-dd-forwarder-<VERSION>.zip` を使用して Python 3.7 Lambda 関数を作成します。
2. Datadog API キーを AWS Secrets Manager に保存し、環境変数 `DD_API_KEY_SECRET_ARN` に Lambda 関数のシークレット ARN を設定し、Lambda 実行ロールに `secretsmanager:GetSecretValue` アクセス許可を追加します。
3. S3 バケットからログを転送する必要がある場合は、`s3:GetObject` アクセス許可を Lambda 実行ロールに追加します。
4. Forwarder で環境変数 `DD_ENHANCED_METRICS` を `false` に設定します。これにより、Forwarder は拡張メトリクス自体を生成しなくなりますが、他の Lambda からカスタムメトリクスを転送します。
5. [トリガー](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#send-aws-service-logs-to-datadog)を構成します。

<!-- xxz tab xxx -->
<!-- xxz tabs xxx -->

## AWS PrivateLink サポート

AWS PrivateLink を使用して、VPC で Forwarder を実行できます。

1. [セットアップ手順](https://docs.datadoghq.com/agent/guide/private-link/?tab=logs#create-your-vpc-endpoint)に従って、Datadog の **API** エンドポイントを VPC に追加します。
2. [同じ手順](https://docs.datadoghq.com/agent/guide/private-link/?tab=logs#create-your-vpc-endpoint)に従って、Datadog の **Logs** エンドポイントを VPC に追加します。
3. デフォルトで、Forwarder の API キーは Secrets Manager に保存されます。Secrets Manager のエンドポイントを VPC に追加する必要があります。手順に従い、[AWS サービスを VPC に追加](https://docs.aws.amazon.com/vpc/latest/userguide/vpce-interface.html#create-interface-endpoint)してください。
4. CloudFormation テンプレートで Forwarder をインストールする際は、'DdUsePrivateLink' を有効にして 1 つ以上の Subnet ID と Security Group を設定してください。

### AWS PrivateLink の制限

* AWS PrivateLink は、Datadog US リージョンの Datadog 組織でのみ構成できます。
* 現在、トレース転送は AWS PrivateLink を介してサポートされていません。

## トラブルシューティング

Forwarder Lambda 関数で環境変数 `DD_LOG_LEVEL` を `debug` に設定して、詳細なログ記録を一時的に有効にします (削除することを忘れないでください)。デバッグログが役に立たない場合は、[Datadog サポート](https://www.datadoghq.com/support/)にお問い合わせください。まだ行っていない場合は、Forwarder を最新バージョンに更新すると役立つ場合があります。

### 新しいバージョンにアップグレードする

1. [datadog-forwarder (名前を変更しなかった場合)](https://console.aws.amazon.com/cloudformation/home#/stacks?filteringText=forwarder) CloudFormation スタックを見つけます。[Datadog AWS インテグレーションスタック](https://github.com/Datadog/cloudformation-template/tree/master/aws)の一部として Forwarder をインストールした場合は、ルートスタックではなく、ネストされた Forwarder スタックを更新してください。
2. CloudFormation スタックの "Resources" タブから実際の Forwarder Lambda 関数を見つけ、そのコンフィギュレーションページに移動します。新しいバージョンで問題が発生し、ロールバックする必要がある場合に備えて、`dd_forwarder_version` タグの値をメモします (例: `3.3.0`)。
3. テンプレート `https://datadog-cloudformation-template.s3.amazonaws.com/aws/forwarder/latest.yaml` を使用してスタックを更新します。必要に応じて、`latest` を特定のバージョン、たとえば `3.0.2.yaml` に置き換えることもできます。更新を適用する前に、変更セットを確認してください。

### 古いバージョンを 3.0.0 以降にアップグレードする

バージョン 3.0.0 以降、Forwarder Lambda 関数は CloudFormation によって管理されます。古い Forwarder のインストールを 3.0.0 以降にアップグレードするには、以下の手順に従います。

1. [インストール](#installation)の手順に従って、新しい Forwarder をインストールします。
2. スタックの "Resources" タブで、論理 ID が `Forwarder` のインストール済みの Forwarder Lambda 関数を見つけます。
3. 古い Forwarder のいくつかのトリガー (CloudWatch ロググループサブスクリプションフィルターと S3 バケットイベント通知) を新しいものに手動で移行します。
4. 新しい Forwarder が期待どおりに機能していること、つまりエラーなしで定期的に呼び出されることを確認します。
5. 移行されたトリガー (ソース) からのログが Datadog ログエクスプローラーに表示されていることと、正しく表示されていることを確認します。
6. すべてのトリガーを新しい Forwarder に移行します。
   - Datadog にトリガーを[自動的](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#automatically-setup-triggers)に管理させる場合は、AWS インテグレーションタイルの "Collect Logs" タブで Forwarder Lambda ARN を更新します。
   - トリガーを[手動](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=allpermissions#manually-setup-triggers)で管理していた場合は、手動で (またはスクリプトを使用して) トリガーを移行する必要があります。
7. 古い Forwarder Lambda 関数の呼び出しカウントがゼロになっていることを確認します。
8. 安心したら、古い Forwarder Lambda 関数を削除します。
9. 古い Forwarder Lambda 関数が複数の AWS アカウントとリージョンにインストールされている場合は、アカウントとリージョンのすべての組み合わせで上記の手順を繰り返します。

### 削除

Forwarder および、Forwarder CloudFormation スタックによって作成された他の AWS リソースを安全に削除するには、以下の手順に従います。

1. [datadog-forwarder (名前を変更しなかった場合)](https://console.aws.amazon.com/cloudformation/home#/stacks?filteringText=forwarder) CloudFormation スタックを見つけます。または、"This function belongs to an application. Click here to manage it." (この関数はアプリケーションに属しています。ここをクリックして管理します。) というメッセージからリンクをクリックし、アプリケーションページの "Deployments" タブをクリックして、Forwarder Lambda 関数の管理コンソールからスタックを見つけることができます。
2. CloudFormation スタックを「削除」します。

### Forwarder 設定の調整

1. [datadog-forwarder (名前を変更しなかった場合)](https://console.aws.amazon.com/cloudformation/home#/stacks?filteringText=forwarder) CloudFormation スタックを見つけます。
2. 現在のテンプレートを使用してスタックを更新します。
3. パラメーター値を調整します。

**注:** Datadog は、Lambda 関数を直接編集するのではなく、CloudFormation を介して Forwarder 設定を調整することをお勧めします。スタックを起動するときに、[template.yaml](template.yaml) と CloudFormation スタック作成ユーザーインターフェイスで設定の説明を確認してください。追加の設定をテンプレートで調整できるように、お気軽にプルリクエストを送信してください。

## アクセス許可

CloudFormation Stack をデフォルトのオプションでデプロイするには、Datadog API キーをシークレットとして保存し、Forwarder のコード (zip ファイル) を格納する S3 バケットを作成し、Lambda 関数 (実行ロールとロググループを含む) を作成します。

**IAM ステートメント**:

```json
{
  "Effect": "Allow",
  "Action": [
    "cloudformation:*",
    "secretsmanager:CreateSecret",
    "secretsmanager:TagResource",
    "s3:CreateBucket",
    "s3:GetObject",
    "s3:PutEncryptionConfiguration",
    "s3:PutBucketPublicAccessBlock",
    "iam:CreateRole",
    "iam:GetRole",
    "iam:PassRole",
    "iam:PutRolePolicy",
    "iam:AttachRolePolicy",
    "lambda:CreateFunction",
    "lambda:GetFunction",
    "lambda:GetFunctionConfiguration",
    "lambda:GetLayerVersion",
    "lambda:InvokeFunction",
    "lambda:PutFunctionConcurrency",
    "lambda:AddPermission",
    "logs:CreateLogGroup",
    "logs:DescribeLogGroups",
    "logs:PutRetentionPolicy"
  ],
  "Resource": "*"
}
```

CloudFormation スタックを作成するには、次の機能が必要です。

- CAPABILITY_AUTO_EXPAND、Forwarder テンプレートはマクロを使用するため (特に [AWS SAM](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/transform-aws-serverless.html) マクロ)
- CAPABILTY_IAM/NAMED_IAM、Forwarder は IAM ロールを作成するため

CloudFormation Stack は、次の IAM ロールを作成します。

- ForwarderRole: Forwarder Lambda 関数が S3 からログを読み取り、Secrets Manager から Datadog API キーをフェッチし、独自のログを書き込むための実行ロール。

**IAM ステートメント**

  ```json
  [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "*"
    },
    {
      "Action": ["s3:GetObject"],
      "Resource": "arn:aws:s3:::*",
      "Effect": "Allow"
    },
    {
      "Action": ["secretsmanager:GetSecretValue"],
      "Resource": "<ARN of DdApiKeySecret>",
      "Effect": "Allow"
    }
  ]
  ```

- `ForwarderZipCopierRole`: ForwarderZipCopier Lambda 関数が S3 バケットに Forwarder デプロイの zip ファイルをダウンロードするための実行ロール。

**IAM ステートメント**:

  ```json
  [
    {
      "Effect": "Allow",
      "Action": [
        "logs:CreateLogGroup",
        "logs:CreateLogStream",
        "logs:PutLogEvents"
      ],
      "Resource": "*"
    },
    {
      "Action": ["s3:PutObject", "s3:DeleteObject"],
      "Resource": "<S3Bucket to Store the Forwarder Zip>",
      "Effect": "Allow"
    },
    {
      "Action": ["s3:ListBucket"],
      "Resource": "<S3Bucket to Store the Forwarder Zip>",
      "Effect": "Allow"
    }
  ]
  ```

## CloudFormation パラメーター

### 必須

- `DdApiKey` - Datadog API キー。これは、Datadog の Integrations > APIs > API Keys にあります。
  API キーは AWS Secrets Manager に保存されます。
- `DdSite` - メトリクスとログの送信先となる Datadog サイト。`datadoghq.com` か
  `datadoghq.eu` のいずれかである必要があります

### Lambda 関数 (オプション)

- `FunctionName` - Datadog Forwarder Lambda 関数の名前。既存の CloudFormation スタックを更新するときは変更しないでください。
  変更すると、現在の Forwarder 関数が置き換えられ、
  すべてのトリガーが失われます。
- `MemorySize` - Datadog Forwarder Lambda 関数のメモリサイズ
- `Timeout` - Datadog Forwarder Lambda 関数のタイムアウト
- `ReservedConcurrency` - Datadog Forwarder Lambda 関数用に予約されている同時実行数
- `LogRetentionInDays` - Datadog Forwarder Lambda 関数によって生成されたログの CloudWatch ログの
  保持


### ログ転送 (オプション)

- `DdTags` - 転送されたログにカスタムタグを追加します。カンマ区切りの文字列で、末尾にカンマはありません。例:
    `env:prod,stack:classic`
- `DdMultilineLogRegexPattern` - 指定された正規表現を使用して、S3 からの複数行ログの新しいログ行を検出します。
  たとえば、パターン "11/10/2014" で始まる複数行ログに対して表現 `\d{2}\/\d{2}\/\d{4}` を
  使用します。
- `DdUseTcp` - デフォルトでは、Forwarder はポート 443 を介して HTTPS を使用してログを送信します。
  SSL 暗号化 TCP 接続を介してログを送信するには、このパラメーターを true に設定します。
- `DdNoSsl` - ログの転送時に SSL を無効にし、プロキシを介してログを転送する場合は true に設定します。
- `DdUrl` - ログを転送するエンドポイント URL。プロキシを介してログを転送するのに役立ちます。
- `DdPort` - ログを転送するエンドポイントポート。プロキシを介してログを転送するのに役立ちます。
- `DdSkipSslValidation` - エンドポイントから指定された証明書を検証せずに、HTTPS 経由でログを送信します。
  これにより、Forwarder とログインテークエンドポイント間のトラフィックは暗号化されますが、
  宛先 SSL 証明書が有効かどうかは検証されません。
- `DdUseCompression` - ログ圧縮を無効にするには、false に設定します。HTTP 経由でログを送信する場合にのみ有効です。
- `DdCompressionLevel` - 圧縮レベルを 0 (圧縮なし) から 9 (最高の圧縮) に設定します。
  デフォルトの圧縮レベルは 6 です。圧縮レベルを上げると、Forwarder の実行時間が長くなる代わりに、
  送信ネットワークトラフィックが減少するという利点が
  あります。
- `DdForwardLog` - ログ転送を無効にするには、false に設定しますが、
  Lambda 関数からのメトリクスやトレースなど、他の可観測性データの転送は続行します。

### ログスクラビング (オプション)

- `RedactIp` - `\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}` に一致するテキストを `xxx.xxx.xxx.xxx` に置き換えます
- `RedactEmail` - `[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+` に一致するテキストを
  `xxxxx@xxxxx.com` に置き換えます
- `DdScrubbingRule` - 指定された正規表現に一致するテキストを `xxxxx` (デフォルト) または `DdScrubbingRuleReplacement` (指定されている場合) に置き換えます。
  ログスクラビングルールは、Lambda 関数によって自動的に追加されるメタデータを含む、完全な JSON 形式のログに適用されます。
  パターン一致の各インスタンスは、
  各ログで一致するものがなくなるまで置き換えられます。
- `DdScrubbingRuleReplacement` - DdScrubbingRule に一致するテキストを、指定されたテキストで置き換えます

### ログのフィルタリング (オプション)

- `ExcludeAtMatch` - 指定された正規表現に一致するログを送信しません。
  ログが ExcludeAtMatch と IncludeAtMatch の両方に一致する場合、そのログは除外されます。
  フィルタリングルールは、関数によって自動的に追加されるメタデータを含む、完全な JSON 形式のログに適用されます。
- `IncludeAtMatch` - 指定された正規表現に一致するログのみを送信し、ExcludeAtMatch によって
  除外されません。

### 試験運用 (オプション)

- `DdFetchLambdaTags` - Forwarder が GetResources API 呼び出しを使用して Lambda タグをフェッチし、
  それらをログ、メトリクス、トレースに適用できるようにします。true に設定すると、アクセス許可 `tag:GetResources` が
  Lambda 実行 IAM ロールに自動的に追加されます。タグはメモリにキャッシュされるため、
  関数がコールドスタートするか、TTL (1 時間) の期限が切れたときにのみフェッチされます。
  Forwarder は、行われた各 API 呼び出しについて、`aws.lambda.enhanced.get_resources_api_calls` メトリクスを増分します。

### 高度 (オプション)

- `SourceZipUrl` - 実行内容を理解できない場合は、変更しないでください。
  関数のソースコードのデフォルトの場所を上書きします。
- `PermissionBoundaryArn` - Permissions Boundary Policy の ARN
- `DdApiKeySecretArn` - Secrets Manager にすでに格納されている場合は、Datadog API キーを格納するシークレットの ARN。
  "DdApiKey" のダミー値を設定して要件を満たす必要がありますが、
  その値は使用されません。
- `DdUsePrivateLink` - AWS PrivateLink を介したログとメトリクスの送信を有効にするには、true に設定します。
  https://dtdg.co/private-link を参照してください。
- `VPCSecurityGroupIds` - VPC セキュリティグループ ID のカンマ区切りリスト。AWS PrivateLink が有効な場合に
  使用されます。
- `VPCSubnetIds` - VPC サブネット ID のカンマ区切りリスト。AWS PrivateLink が有効な場合に使用されます。