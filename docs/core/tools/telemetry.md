---
title: ".NET Core CLI ツールの製品利用統計情報"
description: "利用情報を収集して分析する .NET Core ツールの製品利用統計情報機能と収集されるデータについて、およびこの機能を無効にする方法を説明します。"
keywords: ".NET、.NET Core、製品利用統計情報"
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: HT
ms.sourcegitcommit: c58ed1b3c09f1e358d0b66f6cf7186821601fd69
ms.openlocfilehash: 8ea8ee44a58c6aabfd09afbc7ef53239a9029c57
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---

# <a name="net-core-cli-tools-telemetry"></a>.NET Core CLI ツールの製品利用統計情報

[.NET Core SDK](index.md) には、利用情報を収集する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。 .NET Team がこのツールがどのように利用されているかを理解することが重要です。それにより、ツールが改善されます。 詳細については、「[What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)」 (.NET Core SDK 製品利用統計情報からわかったこと) を参照してください。

収集されたデータは匿名で、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で、Microsoft とコミュニティの両者が利用するために集計された形で公開されます。 

## <a name="scope"></a>スコープ

`dotnet` コマンドは、アプリと .NET Core CLI の両方の起動に使用されます。 `dotnet` コマンド自体は製品利用統計情報を収集しません。 `dotnet` コマンドで実行される .NET Core CLI コマンドが製品利用統計情報を収集します。

コマンドを添付せずに `dotnet` コマンドそのものを使うと、製品利用統計情報は*有効になりません*。

- `dotnet`
- `dotnet [path-to-app]`

次のような [.NET Core CLI コマンド](index.md)を使用すると、製品利用統計情報が*有効になります*。

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="behavior"></a>動作

.NET Core CLI ツールの製品利用統計情報機能は既定では有効になっています。 `DOTNET_CLI_TELEMETRY_OPTOUT` 環境変数を `1` または `true` に設定して、製品利用統計情報の機能をオプトアウトします。

## <a name="data-points"></a>データ ポイント

この機能は次のデータを収集します。

- 呼び出しのタイムスタンプ&#8224;
- 呼び出されたコマンド ("build" など)&#8224;
- 地理的な場所を決定するために使用する 3 つのオクテットの IP アドレス&#8224;
- コマンドの `ExitCode`
- (テスト プロジェクトの) テスト ランナー
- オペレーティング システムとバージョン&#8224;
- ランタイム ノードにランタイム ID が存在するかどうか
- .NET Core SDK バージョン&#8224;

&#8224; このメトリックは公開されています。

.NET Core SDK 2.0 以降では、新しいデータ ポイントが収集されます。

- `dotnet` コマンドの引数とオプション: (任意の文字列ではなく) 既知の引数とオプションのみが収集されます。
- SDK がコンテナーで実行されているかどうか。
- ターゲット フレームワーク。
- ハッシュされた MAC アドレス: 暗号化の面で (SHA256) 匿名であり、マシンの一意の ID。 このメトリックは公開されていません。
- ハッシュされた現在の作業ディレクトリ。

この機能では、ユーザー名やメール アドレスなどの個人データは収集されません。 コードはスキャンされず、名前、リポジトリ、作成者などのプロジェクト レベルの機密データは抽出されません。 データは [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/) テクノロジを使用して Microsoft サーバーに安全に送信され、制限されたアクセスの下で保持され、厳格なセキュリティ コントロールの下で安全な [Azure Storage](https://azure.microsoft.com/services/storage/) システムから公開されます。

ツールで構築しているものではなく、ツールがどのように使われ、問題なく機能しているかどうかを知るためのものです。 利用統計情報で機密情報が収集されているのではないか、またはデータがセキュリティ上問題がある方法でまたは不適切に処理されているのではないかという疑いがある場合は、調査のために [dotnet/cli リポジトリの問題で問題を提起](https://github.com/dotnet/cli/issues)してください。

## <a name="published-data"></a>公開データ

公開データは四半期ごとに利用可能で、「[.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)」 (.NET core SDK の使用状況データ) に一覧表示されます。 データ ファイルの列は次のとおりです。
- タイムスタンプ
- Occurrences&#8224;
- コマンド
- Geography&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224; *Occurrences* 列には、その行のメトリックに対するコマンドの使用回数の、その日の合計数が表示されます。 

&#8225; 通常、*Geography* 列には、国の名前が表示されます。 場合によっては、調査担当者が南極や不正な場所データを使用して .NET Core を使用していることが原因で、この列に南極大陸が表示されることがあります。

### <a name="example"></a>例

| タイムスタンプ      | Occurrences | コマンド | Geography | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | 実行     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>データセット

[2016 - Q3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 - Q4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 - Q1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 - Q2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

追加のデータセットは、標準の URL 形式を使用してポストされます。 `<YEAR>` を年で置き換え、`<QUARTER>` を四半期に置き換えます (`1`、`2`、`3`、 または `4` を使用)。 ファイルはタブ区切り値 (*TSV*) 形式です。 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a>ライセンス

Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。 このライセンスには、製品利用統計情報を有効にするために、次のように "DATA" セクションが含まれています。

[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)は同じライセンスを使用しますが、製品利用統計情報を有効にしません (「[スコープ](#scope)」を参照)。

> 2. データ。 このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。 Microsoft は製品とサービスの向上のために情報を利用することがあります。 データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。 ソフトウェアはこのような慣行に同意した上での利用になります。

## <a name="disclosure"></a>開示

いずれかのコマンド (`dotnet restore` など) をはじめて実行するときに、.NET Core CLI ツールでは次のテキストが表示されます。 テキストは、実行している SDK のバージョンによって多少異なります。 この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a>関連項目

[.NET Core SDK 製品利用統計情報からわかったこと](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[製品利用統計情報の参照のソース (dotnet/cli リポジトリ、リリース/2.0.0 ブランチ)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs)   
[.NET core SDK の使用状況データ](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)

