---
title: ".NET Core ツールの製品利用統計情報 | Microsoft Docs"
description: .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: b7de81f38c0d4fa259f1c9d8ada675197930e945
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---

<a id="net-core-tools-telemetry" class="xliff"></a>

# .NET Core ツールの製品利用統計情報

.NET Core ツールには、利用情報を回収する[製品利用統計情報機能](https://github.com/dotnet/cli/pull/2145)があります。 .NET Team がこのツールの利用方法を理解しておくことが重要です。それにより、ツールが改善されます。

回収されたデータは匿名であり、集計された上で公開され、[Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/) の下で Microsoft エンジニアとコミュニティ エンジニアの両者により利用されます。

<a id="scope" class="xliff"></a>

## スコープ

`dotnet` コマンドは、アプリと .NET Core ツールの両方の起動に使用されます。 `dotnet` コマンド自体は製品利用統計情報を回収しません。 `dotnet` コマンドを介して実行される .NET Core ツールが製品利用統計情報を回収します。

.NET Core コマンド (製品利用統計情報は無効):

- `dotnet`
- `dotnet [path-to-app]`

.NET Core ツールの[コマンド](index.md) (製品利用統計情報は有効):

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

<a id="behavior" class="xliff"></a>

## 動作

.NET Core ツールの製品利用統計情報機能は既定では有効になっています。 製品利用統計情報機能は選択しないこともできます。その場合、環境変数 DOTNET_CLI_TELEMETRY_OPTOUT (たとえば、macOS/Linux の場合は `export`、Windows の場合は `set`) を true ("true" や 1 など) に設定します。

<a id="data-points" class="xliff"></a>

## データ ポイント

この機能は次のデータを回収します。

- 使用されているコマンド ("build" や "restore" など)
- コマンドの ExitCode
- テスト プロジェクトの場合、使用されているテスト ランナー
- 呼び出しのタイムスタンプ
- 使用されているフレームワーク
- "ランタイム" ノードにランタイム ID が存在するかどうか
- 使用されている CLI バージョン

この機能では、ユーザー名や電子メールなど、個人データは回収されません。 コードをスキャンすることはありません。(project.json に設定している場合) 名前、リポジトリ、作成者など、機密と見なされるプロジェクト レベルのデータを抽出することはありません。 ツールで構築しているものではなく、ツールの使われ方を知るためのものです。 機密データが回収された場合、それはバグです。 [問題を提出する](https://github.com/dotnet/cli/issues)と、解決されます。

<a id="license" class="xliff"></a>

## ライセンス

Microsoft による .NET Core の配信は、[MICROSOFT .NET LIBRARY EULA](https://aka.ms/dotnet-core-eula) でライセンス供与されます。 製品利用統計情報を有効にするために、下のように "DATA" セクションが再プリントされます。

[.NET NuGet パッケージ](https://www.nuget.org/profiles/dotnetframework)はこの同じライセンスを使用しますが、製品利用統計情報を有効にしません (上の「[範囲](#scope)」を参照)。

> 2. データ。 このソフトウェアはユーザーとユーザーによるソフトウェアの使用状況に関するデータを収集し、Microsoft に送信する場合があります。 Microsoft は製品とサービスの向上のために情報を利用することがあります。 データの収集と使用状況に関する詳細はヘルプ文書やプライバシーに関する声明 (http://go.microsoft.com/fwlink/?LinkId=528096) で確認できます。 ソフトウェアはこのような慣行に同意した上での利用になります。

<a id="disclosure" class="xliff"></a>

## 開示

いずれかのコマンド (`dotnet restore` など) を始めて実行すると、.NET Core ツールでは次のテキストが表示されます。 この "最初の実行" の際に、Microsoft がデータ回収に関して通知する方法が示されます。 また、このとき、NET Core SDK のライブラリが NuGet キャッシュに入力されます。それらのライブラリに関する NuGet.org への要求 (あるいはその他の NuGet フィード) が回避されます。

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

