---
title: .NET Core の配布パッケージ
description: .NET Core を配布用にパッケージ化、名前付け、およびバージョン管理する方法について説明します。
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 084de6bbb3ce280beb0846431aeceacbb57d9a32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217403"
---
# <a name="net-core-distribution-packaging"></a>.NET Core の配布パッケージ

.NET Core はますます多くのプラットフォームで使用できるようになってきているため、.NET Core をパッケージ化し、名前を付け、バージョン管理する方法を知っていると便利です。 そうすることで、パッケージの管理者は、ユーザーの .NET の実行環境に左右されることなく一貫した体験が保証されるようにサポートできます。

## <a name="disk-layout"></a>ディスク レイアウト

インストールした .NET Core は複数のコンポーネントで構成されています。コンポーネントは、ファイルシステムで次のようにレイアウトされています。

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** ホスト (別名 "muxer (マルチプレクサー)") には 2 つの異なるロールがあります。アプリケーションを起動するランタイムのアクティブ化と、コマンドをディスパッチする SDK のアクティブ化です。 ホストはネイティブの実行可能ファイルです (`dotnet.exe`)。

ホストは 1 つですが、他のコンポーネントのほとんどはバージョン管理されたディレクトリに入っています (2、3、5、6)。 並列インストールされており、複数のバージョンをシステムに置くことができます。

- (2) **host/fxr/\<fxr バージョン>** には、ホストが使用するフレームワーク解決ロジックが含まれます。 ホストでは、インストールされている最新の hostfxr が使用されます。 hostfxr は、.NET Core アプリケーションの実行時に適切なランタイムを選択する役割を担います。 たとえば、.NET Core 2.0.0 用としてビルドされたアプリケーションは、2.0.5 が利用できればそれを利用します。 同様に、hostfxr は開発中、適切な SDK を選択します。

- (3) **sdk/\<sdk バージョン>** SDK (別名 "ツール") は、.NET Core のライブラリやアプリケーションを記述し、ビルドするために使用できるマネージ ツールのセットです。 SDK には、CLI、Roslyn コンパイラ、MSBuild、関連するビルド タスクとターゲット、NuGet、新しいプロジェクト テンプレートなどが含まれています。

- (4) **sdk/NuGetFallbackFolder** には、`dotnet restore` 手順中、SDK で使用される NuGet パッケージのキャッシュが含まれています。

**共有**フォルダーには、フレームワークが含まれています。 共有フレームワークは、さまざまなアプリケーションで利用できるように、中央の場所で一連のライブラリを提供します。

- (5) **shared/Microsoft.NETCore.App/\<runtime バージョン>** このフレームワークには、.NET Core のランタイムと補助マネージ ライブラリが含まれています。

- (6,7) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore バージョン>** には、ASP.NET Core ライブラリが含まれています。 `Microsoft.AspNetCore.App` の下にあるライブラリは、.NET Core プロジェクトの一部として開発され、サポートされています。 `Microsoft.AspNetCore.All` の下にあるライブラリは、サードパーティ ライブラリも含まれるスーパーセットです。

- (8) **LICENSE.txt,ThirdPartyNotices.txt** は .NET Core ライセンスと、.NET Core で利用されるサードパーティ ライブラリのライセンスです。

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` は dotnet man ページです。 `dotnet` は dotnet host(1) のシンボリック リンクです。 これらのファイルは、システム統合のために、よく知られている場所にインストールされます。

## <a name="recommended-packages"></a>推奨パッケージ

.NET Core バージョン管理は、ランタイム コンポーネント `[major].[minor]` バージョン番号に基づきます。
SDK バージョンは同じ `[major].[minor]` を利用し、SDK の機能とパッチ意味論を結合する非依存の `[patch]` が与えられます。
例: SDK バージョン 2.2.302 は、2.2 ランタイム対応の SDK の第 3 機能リリースの第 2 パッチ リリースです。

パッケージには、その名前にバージョン番号の一部が含まれているものもあります。 それによって、エンドユーザーは特定のバージョンをインストールできます。
バージョンの残りの部分はバージョン名には含まれていません。 それによって、OS パッケージ マネージャーはパッケージを更新できます (セキュリティ修正の自動インストールなど)。

次の表は、推奨パッケージをまとめたものです。

| name                                    | 例                | ユース ケース: インストール ...           | 内容           | 依存関係                                   | Version            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | ランタイム メジャーの最新 sdk    |                    | dotnet-sdk-[major].[latestminor]               | \<sdk version>     |
| dotnet-sdk-[major].[minor]              | dotnet-sdk-2.1         | 特定のランタイムの最新の sdk |                    | dotnet-sdk-[major].[minor].[latest sdk feat]xx | \<sdk version>     |
| dotnet-sdk-[major].[minor].[sdk feat]xx | dotnet-sdk-2.1.3xx     | 特定の sdk 機能リリース    | (3),(4)            | aspnetcore-runtime-[major].[minor]             | \<sdk version>     |
| aspnetcore-runtime-[major].[minor]      | aspnetcore-runtime-2.1 | 特定の ASP.NET Core ランタイム   | (6),[(7)]          | dotnet-runtime-[major].[minor]                 | \<runtime version> |
| dotnet-runtime-[major].[minor]          | dotnet-runtime-2.1     | 特定のランタイム                | (5)                | host-fxr:\<runtime version>+                   | \<runtime version> |
| dotnet-host-fxr                         | dotnet-host-fxr        | _dependency_                    | (2)                | host:\<runtime version>+                       | \<runtime version> |
| dotnet-host                             | dotnet-host            | _dependency_                    | (1),(8),(9),(10)   |                                                | \<runtime version> |

ほとんどのディストリビューションで、ソースからビルドするすべての成果物を必要とします。 これはパッケージにいくつかの影響を与えます。

- `shared/Microsoft.AspNetCore.All` の下にあるサードパーティ ライブラリは、ソースから簡単にビルドできません。 そのため、そのフォルダーは `aspnetcore-runtime` パッケージから除外されます。

- `NuGetFallbackFolder` は `nuget.org` からバイナリ成果物を利用して入力されます。 空のままにしてください。

複数の `dotnet-sdk` パッケージで `NuGetFallbackFolder` に同じファイルが提供されることがあります。 パッケージ マネージャーの問題を回避するには、これらのファイルを同じにします (チェックサム、変更日...)。

#### <a name="preview-versions"></a>プレビュー バージョン

パッケージ管理者は、共有フレームワークと SDK のプレビュー バージョンを提供するという選択もできます。 プレビュー リリースは、`dotnet-sdk-[major].[minor].[sdk feat]xx`、`aspnetcore-runtime-[major].[minor]`、`dotnet-runtime-[major].[minor]` パッケージを利用して提供されることもあります。 プレビュー リリースの場合、パッケージ バージョン メジャーをゼロに設定する必要があります。 この方法で、最終リリースがパッケージのアップグレードとしてインストールされます。

#### <a name="patch-packages"></a>パッチ パッケージ

パッケージのパッチ バージョンは破壊的な変更を招くことがあるため、パッケージ管理者は_パッチ パッケージ_を提供することがあります。 そのようなパッケージによって、自動的にアップグレードされない特定のパッチ バージョンをインストールできます。 パッチ パッケージは (セキュリティ) 修正でアップグレードされないため、まれな状況でのみ使用してください。

次の表は、推奨パッケージと**パッチ パッケージ**をまとめたものです。

| name                                           | 例                  | 内容         | 依存関係                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | dotnet-sdk-[major].[latest sdk minor]                     |
| dotnet-sdk-[major].[minor]                     | dotnet-sdk-2.1           |                  | dotnet-sdk-[major].[minor].[latest sdk feat]xx            |
| dotnet-sdk-[major].[minor].[sdk feat]xx        | dotnet-sdk-2.1.3xx       |                  | dotnet-sdk-[major].[minor].[latest sdk patch]             |
| **dotnet-sdk-[major].[minor].[patch]**         | dotnet-sdk-2.1.300       | (3),(4)          | aspnetcore-runtime-[major].[minor].[sdk runtime patch]    |
| aspnetcore-runtime-[major].[minor]             | aspnetcore-runtime-2.1   |                  | aspnetcore-runtime-[major].[minor].[latest runtime patch] |
| **aspnetcore-runtime-[major].[minor].[patch]** | aspnetcore-runtime-2.1.0 | (6),[(7)]        | dotnet-runtime-[major].[minor].[patch]                    |
| dotnet-runtime-[major].[minor]                 | dotnet-runtime-2.1       |                  | dotnet-runtime-[major].[minor].[latest runtime patch]     |
| **dotnet-runtime-[major].[minor].[patch]**     | dotnet-runtime-2.1.0     | (5)              | host-fxr:\<runtime version>+                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | host:\<runtime version>+                                  |
| dotnet-host                                    | dotnet-host              | (1),(8),(9),(10) |                                                           |

パッチ パッケージの使用の代わりになるのが_ピン留め_ (固定) です。パッケージ マネージャーを利用し、特定のバージョンにパッケージを固定します。 他のアプリケーション/ユーザーに影響を与えないように、このようなアプリケーションはコンテナーでビルドし、配置できます。

## <a name="building-packages"></a>パッケージをビルドする

https://github.com/dotnet/source-build リポジトリには、.NET Core SDK のソース ターボールとそのすべてのコンポーネントをビルドする方法があります。 この source-build リポジトリの出力は、この記事の最初のセクションで説明したレイアウトに一致します。