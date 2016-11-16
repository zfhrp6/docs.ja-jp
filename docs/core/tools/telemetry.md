---
title: ".NET Core ツールの製品利用統計情報"
description: .NET Core
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 07/06/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f2b312bb-f80b-4b0d-9101-93908f06a6fa
translationtype: Human Translation
ms.sourcegitcommit: c53c7d3b5733e15e066fd975bf3fa414ee96bbd1
ms.openlocfilehash: 4717b1f608051dc748ba3f1ceb94d6ddd94250bb

---

# <a name="net-core-tools-telemetry"></a>.NET Core ツールの製品利用統計情報

.NET Core ツールには、利用情報を回収する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。 .NET Team がこのツールの利用方法を理解しておくことが重要です。それにより、ツールが改善されます。

回収されたデータは匿名であり、集計された上で公開され、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で Microsoft エンジニアとコミュニティ エンジニアの両者により利用されます。

## <a name="scope"></a>スコープ

`dotnet` コマンドは、アプリと .NET Core ツールの両方の起動に使用されます。 `dotnet` コマンド自体は製品利用統計情報を回収しません。 `dotnet` コマンドを介して実行される .NET Core ツールが製品利用統計情報を回収します。

.NET Core コマンド (製品利用統計情報は無効):

- `dotnet`
- `dotnet [path-to-app]`

.NET Core ツールの[コマンド](index.md) (製品利用統計情報は有効):

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

##<a name="behavior"></a>動作

.NET Core ツールの製品利用統計情報機能は既定では有効になっています。 製品利用統計情報機能は選択しないこともできます。その場合、環境変数 DOTNET_CLI_TELEMETRY_OPTOUT (たとえば、macOS/Linux の場合は `export`、Windows の場合は `set`) を true (“true” や 1 など) に設定します。

##<a name="data-points"></a>データ ポイント

この機能は次のデータを回収します。

- 使用されているコマンド (“build” や “restore” など)
- コマンドの ExitCode
- テスト プロジェクトの場合、使用されているテスト ランナー
- 呼び出しのタイムスタンプ
- 使用されているフレームワーク
- “ランタイム” ノードにランタイム ID が存在するかどうか
- 使用されている CLI バージョン

この機能では、ユーザー名や電子メールなど、個人データは回収されません。 コードをスキャンすることはありません。(project.json に設定している場合) 名前、リポジトリ、作成者など、機密と見なされるプロジェクト レベルのデータを抽出することはありません。 ツールで構築しているものではなく、ツールの使われ方を知るためのものです。 機密データが回収された場合、それはバグです。 [問題を提出する](https://github.com/dotnet/cli/issues)と、解決されます。

##<a name="license"></a>ライセンス

Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。 製品利用統計情報を有効にするために、下のように “DATA” セクションが再プリントされます。

[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)はこの同じライセンスを使用しますが、製品利用統計情報を有効にしません (上の「[範囲](#scope)」を参照)。

```text
2.      DATA.  The software may collect information about you and your use of
the software, and send that to Microsoft. Microsoft may use this information
to improve our products and services. You can learn more about data collection
and use in the help documentation and the privacy statement at
http://go.microsoft.com/fwlink/?LinkId=528096 . Your use of the software
operates as your consent to these practices.
```

## <a name="disclosure"></a>開示

いずれかのコマンド (`dotnet restore` など) を始めて実行すると、.NET Core ツールでは次のテキストが表示されます。 この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。 また、このとき、NET Core SDK のライブラリが NuGet キャッシュに入力されます。それらのライブラリに関する NuGet.org への要求 (あるいはその他の NuGet フィード) が回避されます。

```text
Welcome to .NET Core!
---------------------

Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to
see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
---------

The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include commandline arguments. The data is
collected by Microsoft and shared with the community.

You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT
environment variable to 1 using your favorite shell.

You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-
telemetry.

Configuring...
--------------

A command is running to initially populate your local package cache, to
improve restore speed and enable offline access. This command will take up to
a minute to complete and will only happen once. 
```



<!--HONumber=Nov16_HO1-->


