---
title: .NET Core バージョン管理
description: .NET Core でのバージョン管理のしくみについて説明します。
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: 0cfd620d2b6e6e60531b0e2aa938c1ed64b6af23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-versioning"></a>.NET Core バージョン管理

.NET Core は、ユニットとして配布される [NuGet パッケージ](../packages.md)、ツール、フレームワークで構成されます。 これらのプラットフォームの各レイヤーは、製品のアジリティ向上のため、個別にバージョン管理できます。 バージョン管理には大きな柔軟性がありますが、製品を理解しやすいように、プラットフォームをユニットとしてバージョン管理することも望まれています。

この記事では、.NET Core SDK とランタイムのバージョン管理方法を明確にすることを目的としています。

.NET Core には個別にバージョン管理される多くの移動するパーツがあります。 ただし、.NET Core 2.0 以降では、すべてのユーザーが ".NET Core" 全体のバージョンとして理解する簡単に理解できる最上位*レベ*ルのバージョンがあります。 このドキュメントの残りの部分は、これらすべてのパーツのバージョン管理の詳細について説明します。 たとえばパッケージ マネージャーの場合は、これらの詳細が重要になる可能性があります。

> [!IMPORTANT]
> このトピックで説明されているバージョン管理の詳細は、.NET Core SDK ランタイムの現在のバージョンには適用されません。
> バージョン スキームは将来のリリースで変更されます。 [dotnet/designs](https://github.com/dotnet/designs/pull/29) リポジトリで現在の提案を表示できます。

## <a name="versioning-details"></a>バージョン管理の詳細

.NET Core 2.0 では、ダウンロードは、ファイル名に 1 つのバージョン番号が表示されます。 次のバージョン番号が統合されました。

* 共有のフレームワークおよび関連付けられているランタイム。
* .NET Core SDK および関連付けられた .NET Core CLI。
* `Microsoft.NETCore.App` メタパッケージ。

1 つのバージョン番号を使用すると、ユーザーが自分のデバイス マシンにインストールする SDK のバージョン、および運用環境にプロビジョニングするときの共有フレームワークの対応するバージョンを簡単に知ることができるようになります。 SDK またはランタイムをダウンロードするときに、表示されるバージョン番号は同じです。

### <a name="installers"></a>インストーラー

.NET Core 2.0 では、[日次のビルド](https://github.com/dotnet/core-setup#daily-builds)と[リリース](https://www.microsoft.com/net/download/core)は、理解しやすい新しい名前付けスキームに従います。
これらのダウンロードのインストーラー UI も、インストールされているコンポーネントの名前とバージョンを明確に表示するように変更されました。 具体的には、タイトルは、ダウンロードのファイル名に含まれるものと同じバージョン番号を表示するようになりました。

#### <a name="file-name-format"></a>ファイル名の形式

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

この形式のいくつかの例を次に示します。

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

形式は読み取り可能であり、ダウンロードしている内容、そのバージョン、それらを使用できる場所を明確に示します。 ランタイム パッケージ名には、`runtime` が含まれ、SDK には `SDK` が含まれます。

#### <a name="ui-string-format"></a>UI の文字列形式

すべての Web サイトの説明と、インストーラーの UI 文字列では一貫性、正確さ、簡潔さが維持されています。 次の表に例を示します。

| Installer | ウィンドウ タイトル                          | インストーラーの他のコンテンツ | インストールされる内容                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | .NET Core 2.0 (x64) SDK インストーラー     | .NET Core 2.0.4 SDK        | .NET Core 2.0.4 ツール + .NET Core 2.0.4 ランタイム |
| ランタイム   | .NET Core 2.0 ランタイム (x64) インストーラー | .NET Core 2.0.4 ランタイム    | .NET Core 2.0.4 ランタイム                         |

プレビュー リリースはわずかに異なります。

| Installer | ウィンドウ タイトル                                    | インストーラーの他のコンテンツ        | インストールされる内容                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | .NET Core 2.0 Preview 1 SDK (x 64) インストーラー     | .NET Core 2.0.0 Preview 1 SDK     | .NET Core 2.0.0 Preview 1 ツール + .NET Core 2.0.0 Preview 1 ランタイム |
| ランタイム   | .NET Core 2.0 Preview 1 ランタイム (x64) インストーラー | .NET Core 2.0.0 Preview 1 ランタイム | .NET Core 2.0.0 Preview 1 ランタイム                                   |

1 つの SDK リリースに複数のランタイムのバージョンが含まれている可能性があります。 その場合、インストーラー UI は次のようになります (SDK のバージョンのみが表示され、インストールされるランタイムのバージョンは、Windows および Mac でのインストール処理の最後にある概要ページに表示されます)。

| Installer | ウィンドウ タイトル                      | インストーラーの他のコンテンツ                                   | インストールされる内容                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | .NET Core 2.1 SDK (x64) インストーラー | .NET Core 2.1.1 SDK <br> .NET Core 2.1.1 ランタイム <br> .NET Core 2.0.6 ランタイム | .NET Core 2.1.1 ツール + .NET Core 2.1.1 ランタイム + .NET Core 2.0.6 ランタイム |

ランタイムを変更せずに、.NET Core ツールを更新する必要がある場合もあります。 この場合、SDK のバージョンが増加し (たとえば 2.1.2 になり)、ランタイムは次回の配布時に更新されます (たとえば、ランタイムと SDK の両方が次回に 2.1.3 として配布されます)。

### <a name="package-managers"></a>パッケージ マネージャー

.NET Core は、Microsoft 以外のエンティティによって配布される場合があります。 具体的には、Linux ディストリビューションの所有者とパッケージ管理者は、自社のパッケージ マネージャーに .NET Core パッケージを追加する場合があります。 これらのパッケージの命名方法に関する推奨事項については、「[.NET Core distribution packaging](../build/distribution-packaging.md)」(.NET Core の配布パッケージ) を参照してください。

#### <a name="minimum-package-set"></a>最小パッケージ セット

* `dotnet-runtime-[major].[minor]`: 指定したバージョンのランタイム (パッケージ マネージャーでは、指定したメジャーとマイナーの組み合わせからなる最新パッチ バージョンのみ使用可能)。 新しいパッチ バージョンでパッケージを更新しますが、新しいマイナーまたはメジャー バージョンは別のパッケージとなります。

  **依存関係**: `dotnet-host`

* `dotnet-sdk`: 最新の SDK `update` がメジャー、マイナー、およびパッチ バージョンをロール フォワードします。

  **依存関係**: 最新の `dotnet-sdk-[major].[minor]`

* `dotnet-sdk-[major].[minor]`: 指定したバージョンの SDK 指定するバージョンは、ユーザーが共有フレームワークに SDK を簡単に関連付けられるように、同梱する共有フレームワークの中で最も高いバージョンを含むものにします。 新しいパッチ バージョンでパッケージを更新しますが、新しいマイナーまたはメジャー バージョンは別のパッケージとなります。

  **依存関係**: `dotnet-host`、1 つまたは複数の `dotnet-runtime-[major].[minor]` (そのうちの 1 つは SDK コード自体で使用され、それ以外はユーザーの構築および実行のためにこの場所にあります)。

* `dotnet-host`: 最新のホスト

##### <a name="preview-versions"></a>プレビュー バージョン

パッケージ管理者は、ランタイムと SDK のプレビュー バージョンを含めるという選択もできます。 それらのプレビュー バージョンはバージョン管理されない `dotnet-sdk` パッケージに含めないでください。ただし、名前のメジャーおよびマイナー バージョン セクションにプレビュー マーカーを追加して、バージョン管理されたパッケージとしてリリースできます。 たとえば、`dotnet-sdk-2.0-preview1-final` のようなパッケージが可能です。

### <a name="docker"></a>Docker

一般的な Docker タグの名前付け規則では、コンポーネント名の前にバージョン番号を配置します。 この規則は、引き続き利用できます。 現在のタグには、次のようにランタイムのバージョンのみが含まれます。

* 1.0.8-runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-runtime
* 2.1.1-sdk

ランタイムではなく、SDK のバージョンを表すように SDK のタグを更新する必要があります。

.NET Core CLI ツール (SDK に含まれる) が修正される可能性がありますが、既存のランタイムとともに再出荷されます。 この場合、SDK のバージョンが増加し (たとえば 2.1.2 になり)、ランタイムは次回の配布時に更新されます (たとえば、ランタイムと SDK の両方が次回に 2.1.3 として配布されます)。

## <a name="semantic-versioning"></a>セマンティック バージョン管理

.NET Core は、[セマンティック バージョン管理 (SemVer)](http://semver.org/) を使用して、`MAJOR.MINOR.PATCH` バージョン管理を採用し、バージョン番号のさまざまな部分を使用して変更の度合いと種類を記述します。

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

省略可能な `PRERELEASE` と `BUILDNUMBER` の部分はサポートされるリリースに含まれることはなく、ソース ターゲットからローカルでビルドされた夜間のビルドおよびサポートされていないプレビュー リリースにのみ存在します。

### <a name="how-version-numbers-are-incremented"></a>バージョン番号はどのように増分されますか?

`MAJOR` は次のときに増分されます。

- 古いバージョンがサポート対象から除外された。
- 既存の依存関係の新しい `MAJOR` バージョンが採用された。
- 互換性特性の既定の設定が "オフ" に変更された。

`MINOR` は次のときに増分されます。

- パブリック API アクセス領域が追加された。
- 新しい動作が追加された。
- 既存の依存関係の新しい `MINOR` バージョンが採用された。
- 新しい依存関係が導入された。

`PATCH` は次のときに増分されます。

- バグの修正が行われた。
- より新しいプラットフォームのサポートが追加された。
- 既存の依存関係の新しい `PATCH` バージョンが採用された。
- 前のケースのいずれかに一致しない他の変更。

複数の変更が存在する場合、個々の変更によって影響を受ける最高位置の要素が増分され、それに続く要素はゼロにリセットされます。 たとえば、`MAJOR` が増分され、`MINOR` と `PATCH` はゼロにリセットされます。 `MINOR` が増分されるときには、`PATCH` はゼロにリセットされますが、`MAJOR` は変更されません。

### <a name="preview-versions"></a>プレビュー バージョン

プレビュー バージョンには、`-preview[number]-([build]|"final")` がバージョンに追加されます。 たとえば、`2.0.0-preview1-final` のようにします。

### <a name="servicing-versions"></a>サービスのバージョン

リリースされると、通常はリリース ブランチが毎日のビルドの生成を停止し、代わりにサービスのビルドの生成を開始します。 サービスのバージョンには、`-servicing-[number]` がバージョンに追加されます。 たとえば、`2.0.1-servicing-006924` のようにします。

### <a name="lts-vs-current"></a>LTS と Current

.NET Core のリリースには、Long Term Support (LTS) と Current という 2 つのリリース トレーニングがあります。 これにより、ユーザーは、引き続きサポートされているときに、安定性のレベルと必要な新機能を選択することができます。

- LTS は、新機能を受け取る頻度が低くとも、より完成度の高いプラットフォームを利用できることを意味します。 LTS では、長期間のサポートもあります。
- Current は、新機能と API をより頻繁に取得しますが、更新プログラムをインストールするための期間が短く、それらの更新がより頻繁に発生するという欠点があります。 Current も完全にサポートされていますが、サポート期間が LTS よりも短くなっています。

"Current" バージョンは LTS に昇格される場合があります。

"LTS" と "Current" は、関連付けられているレベルのサポートに関するステートメントを指定するために特定のリリースに付けるラベルと見なす必要があります。

詳細については、[.NET Core サポート ライフサイクル ファクト シート](https://www.microsoft.com/net/core/support)を参照してください。

## <a name="versioning-scheme-details"></a>バージョン管理スキームの詳細

.NET Core は、次の部分で構成されます。

- ホスト: フレームワークに依存するアプリケーション用の *dotnet.exe*、または自己完結型アプリケーション用の *\<appname > .exe* です。
- SDK (実稼働環境ではなく開発者のマシンに必要な一連のツール)。
- ランタイム。
- パッケージとして配布される共有フレームワークの実装。 特に修正プログラムのバージョン管理において、各パッケージは個別にバージョン管理されます。
- または、バージョン管理されたユニットとして詳細なパッケージを参照する[メタパッケージ](../packages.md)のセット。 メタパッケージは、パッケージとは別個にバージョン管理できます。

.NET Core には、ターゲット フレームワークのセットも含まれています (たとえば、`netstandard` または `netcoreapp`)。これはバージョン番号の増分と共に徐々に大きくなる API セットを表します。

### <a name="net-standard"></a>.NET Standard

.NET Standard では、`MAJOR.MINOR` バージョン管理スキームを使用しています。 `PATCH` レベルは、.NET Standard では使用できません。これは、あまり頻繁に反復処理されないコントラクトのセットを表し、実際の実装と同じバージョン管理の要件を表さないためです。

.NET Standard バージョンと .NET Core のバージョンの間に実際の結合はありません。 .NET Core 2.0 は .NET Standard 2.0 を実装する場合がありますが、.NET Core の将来のバージョンが同じ .NET Standard のバージョンにマッピングされるという保証はありません。 .NET Core は、.NET Standard で定義されていない API を配布することができるので、新しい .NET Standard を必要とせずに新しバージョンを配布する場合があります。 .NET Standard は、たとえその始まりが .NET Core と同時に起こったとしても、.NET Framework や Mono などの他のターゲットに適用される概念でもあります。

### <a name="packages"></a>パッケージ

ライブラリ パッケージは独立して進化し、バージョン管理されます。 .NET Framework System.\* アセンブリと重複するパッケージは、通常は 4.x バージョンを使用し、.NET Framework 4.x のバージョン管理 (履歴選択) に適合します。 .NET Framework ライブラリと重複しないパッケージ (たとえば、[`System.Reflection.Metadata`](https://www.nuget.org/packages/System.Reflection.Metadata)) は、通常は 1.0 から開始し、増分していきます。

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) によって記述されるパッケージは、プラットフォームのベースに位置するので、特別に扱われます。

`NETStandard.Library` パッケージは、それらの間に実装レベルの依存関係があるため、通常はセットとしてバージョン管理されます。

### <a name="metapackages"></a>メタパッケージ

.NET Core メタパッケージのバージョン管理は、それが含まれている .NET Core バージョンに基づいています。

たとえば、.NET Core 2.1.3 のメタパッケージの `MAJOR` と `MINOR` のバージョン番号はすべて 2.1 になります。

メタパッケージの修正プログラムのバージョンは、参照されるパッケージが更新されるたびに増分されます。 修正プログラムのバージョンには、更新されたフレームワークのバージョンは含まれません。 したがって、メタパッケージは、厳密には SemVer 準拠であると言えません。そのバージョン管理スキームが、基になるパッケージでの変更の度合いを表さず、主に API レベルであるためです。

.NET Core には、現在、次の 2 の主なメタパッケージがあります。

**Microsoft.NETCore.App**

- .NET Core 1.0 の場合は v1.0 (これらのバージョンは一致します)。
- `netcoreapp` フレームワークにマップされます。
- .NET Core 配布に含まれるパッケージを記述します。

注: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) は、NET Standard の前の .NET の実装との互換性を可能にするために存在する .NET Core メタパッケージです。 特定のフレームワークにマップされないため、パッケージのようにバージョン管理されます。

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) は [.NET Standard](../../standard/library.md) に含まれるライブラリを記述したものです。 .NET Standard をサポートするすべての .NET 実装 (.NET Framework、.NET Core、Mono など) に適用されます。

### <a name="target-frameworks"></a>ターゲット フレームワーク

ターゲット フレームワーク バージョンは、新しい API が追加されると更新されます。 これらは API のシェイプを表し、実装には関係しないので、修正プログラム バージョンの概念はありません。 メジャーおよびマイナーのバージョン管理は、前に指定した SemVer 規則に従い、それらを実装する .NET Core ディストリビューションの `MAJOR` および `MINOR` の番号と一致します。

## <a name="versioning-in-practice"></a>実際のバージョン管理

.NET Core をダウンロードするときには、たとえば `dotnet-sdk-2.0.4-win10-x64.exe` のように、ダウンロードするファイルの名前にバージョンが指定されます。

GitHub の .NET Core リポジトリでは、コミットおよびプル要求が毎日発生し、多くのライブラリの新しいビルドが生成されます。 変更が行われるたびに、.NET Core の新しいパブリック バージョンを作成するのは実用的ではありません。 代わりに、.NET Core の新しいパブリック安定バージョンを作成する前に、未確定の期間 (たとえば、数週間や数か月) にわたって、変更が集計されます。

.NET Core の新しいバージョンは、次の複数の意味を持ちます。

- パッケージおよびメタパッケージの新しいバージョン。
- 新しい API の追加を仮定した場合の、さまざまなフレームワークの新しいバージョン。
- .NET Core 配布の新しいバージョン。

### <a name="shipping-a-patch-release"></a>修正プログラム リリースの配布

バージョン 2.0.0 などの .NET Core のメジャー リリースを配布した後は、バグを修正してパフォーマンスと信頼性を高めるために、.NET Core ライブラリに対して修正プログラム レベルの変更が行われます。 つまり、新しい API は導入されません。 更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 メタパッケージは、修正プログラムの更新 (`MAJOR.MINOR.PATCH`) としてバージョン管理されます。 ターゲット フレームワークは修正プログラムのリリースの一部として更新されません。 新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。

### <a name="shipping-a-minor-release"></a>マイナー リリースの配布

増分された `MAJOR` バージョン番号の .NET Core バージョンを配布した後は、新しいシナリオを有効にするために .NET Core ライブラリに新しい API が追加されます。 更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 メタパッケージは、新しいフレームワークのバージョンと一致する `MAJOR` および `MINOR` のバージョン番号で、修正プログラムの更新としてバージョン管理されます。 新しい `MAJOR.MINOR` バージョンの新しいターゲット フレームワーク名 (たとえば、`netcoreapp2.1`) が、新しい API を記述するために追加されます。 新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。

### <a name="shipping-a-major-release"></a>メジャー リリースの配布

.NET Core の新しいメジャー バージョンが配布されるたびに、`MAJOR` バージョン番号が増分され、`MINOR` バージョン番号が 0 にリセットされます。 新しいメジャー バージョンには、少なくとも前のメジャー バージョン以降にマイナー リリースで追加されたすべての API が含まれています。 新しいメジャー バージョンは重要な新しいシナリオを有効にする必要があり、また古いプラットフォームのサポートを終了する場合があります。

更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) メタパッケージおよび `netcore` ターゲット フレームワークは、新しいリリースの `MAJOR` バージョン番号と一致するメジャー更新プログラムとしてバージョン管理されます。

## <a name="see-also"></a>関連項目

[ターゲット フレームワーク](../../standard/frameworks.md)  
[.NET Core の配布パッケージ](../build/distribution-packaging.md)  
[.NET Core サポート ライフサイクルのファクト シート](https://www.microsoft.com/net/core/support)  
[.NET core 2 + バージョン バインディング](https://github.com/dotnet/designs/issues/3)  
