---
title: .NET Core
description: .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f2b312cb-f80c-4b0d-9101-93908f06a6fa
translationtype: Human Translation
ms.sourcegitcommit: d97a1501ad25b683cbb5d7fbd8bd1b137f7f4046
ms.openlocfilehash: 132551673f97142a90513d43d7690867c3d00295
ms.lasthandoff: 04/10/2017

---

# <a name="net-core"></a>.NET Core

> 「[Getting Started](getting-started.md)」 (概要) では、単純な .NET Core アプリケーションを作成する方法を学習できます。 最初のアプリを、ほんの数分で起動および実行できます。

.NET Core は、[GitHub](https://github.com/dotnet/core) で Microsoft および .NET コミュニティによって管理される一般的な開発プラットフォームです。 クロスプラットフォームであり、Windows、macOS、Linux をサポートし、デバイス、クラウド、および埋め込み/IoT シナリオで使用できます。 

.NET Core の典型的な特性は次のとおりです。

- **柔軟な展開:** アプリに含めることも、ユーザー全体またはコンピューター全体に side-by-side (横並び) にインストールすることもできます。
- **クロスプラットフォーム:** Windows、macOS、Linux で実行され、他のオペレーティング システムに移植できます。 [サポートされるオペレーティング システム (OS)](https://github.com/dotnet/core/blob/master/roadmap.md)、CPU、およびアプリケーションのシナリオは Microsoft、その他の企業、および個人によって提供され、時間の経過に伴って増加します。
- **コマンドライン ツール:** 製品のすべてのシナリオは、コマンドラインで実行できます。 
- **互換性:** .NET Core は、[.NET 標準ライブラリ](../standard/library.md)経由で .NET Framework、Xamarin、Mono と互換性があります。
- **オープン ソース:** .NET Core プラットフォームはオープン ソースであり、MIT および Apache 2 ライセンスを使用します。 ドキュメントは [CC-BY](https://creativecommons.org/licenses/by/4.0/) 下でライセンス付与されています。 .NET Core は [.NET Foundation](https://dotnetfoundation.org/) プロジェクトです。
- **Microsoft によるサポート:** .NET Core は、[.NET Core サポート](https://www.microsoft.com/net/core/support/)ごとに Microsoft によってサポートされます。

## <a name="composition"></a>コンポジション

.NET Core は、次の部分で構成されます。

- [.NET ランタイム](https://github.com/dotnet/coreclr)。型システム、アセンブリ読み込み、ガベージ コレクター、ネイティブ相互運用機能、およびその他の基本的なサービスを提供します。 
- 一連の[フレームワーク ライブラリ](https://github.com/dotnet/corefx)。プリミティブ データ型、アプリ コンポジションの種類、および基本的なユーティリティを提供します。 
- [SDK ツールのセット](https://github.com/dotnet/cli)と[言語コンパイラ](https://github.com/dotnet/roslyn)。[.NET Core SDK](sdk.md) に含まれており、ベース開発者エクスペリエンスを有効にします。
- 'dotnet' アプリケ ホスト。.NET Core アプリの起動に使用されます。 ランタイムの選択、ランタイムのホスト、アセンブリ読み込みポリシーの提供、およびアプリの起動を行います。 同じホストが、ほぼ同じ方法で SDK ツールの起動にも使用されます。

### <a name="languages"></a>言語

.NET Core のアプリケーションとライブラリを記述するには、C# および F# 言語を使用できます (Visual Basic も間もなく使用可能になります)。 コンパイラは .NET Core 上で実行され、任意の実行場所で .NET Core 用の開発を可能にします。 一般的に、コンパイラは直接使用せず、SDK ツールを使用して間接的に使用します。

C# および F# コンパイラと .NET Core ツールは、 Visual Studio、[Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)、Sublime Text、Vim などの複数のテキスト エディターおよび IDE に統合されているか、または統合することができます。これにより、任意のコーディング環境および OS で .NET Core 開発を行うことができます。 この統合は、1 つには [OmniSharp プロジェクト](http://www.omnisharp.net/)の優れた要員によって提供されます。

### <a name="net-apis-and-compatibility"></a>.NET API と互換性

.NET Core は、.NET Framework 基本クラス ライブラリ (BCL) のレイヤーでは .NET Framework のクロスプラットフォーム バージョンとして考えることができます。 これは [.NET 標準ライブラリ](../standard/library.md)仕様を実装します。 .NET Core は、.NET Framework または Mono/Xamarin で使用可能な API のサブセットを提供します。 場合によっては、型は完全には実装されません (一部のメンバーが使用できないか、移動されています)。

.NET Core API ロードマップの詳細については、「[.NET Core Roadmap](https://github.com/dotnet/core/blob/master/roadmap.md)」 (.NET Core ロードマップ) を参照してください。

### <a name="relationship-to-the-net-standard-library"></a>.NET 標準ライブラリとの関係

[.NET 標準ライブラリ](../standard/library.md)は、開発者が各 .NET 実装で予想できる .NET API の一貫性のあるセットを表す API 仕様です。 .NET 実装では、.NET 標準ライブラリ準拠と見なされるとともに、標準ライブラリをターゲットとするライブラリをサポートするために、この仕様を実装する必要があります。 

.NET Core は .NET 標準ライブラリを実装するので、.NET 標準ライブラリをサポートしています。

### <a name="workloads"></a>作業負荷

.NET Core 自体には 1 つのアプリケーション モデル (コンソール アプリ) が含まれており、ツール、ローカル サービス、およびテキストベースのゲームに便利です。 次のような機能を拡張するために、.NET Core の上に追加のアプリケーション モデルがビルドされています。

- [ASP.NET Core](https://docs.microsoft.com/aspnet/core/)
- [Windows 10 ユニバーサル Windows プラットフォーム (UWP)](https://developer.microsoft.com/windows)
- [Xamarin.Forms](https://www.xamarin.com/forms)

### <a name="open-source"></a>オープン ソース

[.NET Core](https://github.com/dotnet/core) はオープン ソース (MIT ライセンス) であり、2014 年に Microsoft によって [.NET Foundation](https://dotnetfoundation.org) に提供されたものです。 現在では、最もアクティブな .NET Foundation プロジェクトの 1 つとなっています。 個人、学術、商用などの目的で、個人および企業が自由に採用できます。 複数の企業が、アプリ、ツール、新しいプラットフォーム、およびホスティング サービスの一部として .NET Core を使用しています。 これらの企業の一部は、GitHub の .NET Core に多大な貢献をしており、[.NET Foundation テクニカル ステアリング グループ](https://dotnetfoundation.org/blog/tsg-welcome)の一員として製品の方向性に関するガイダンスを提供しています。

## <a name="acquisition"></a>取得

.NET Core は、NuGet.org でのパッケージとスタンドアロンでの配布という 2 つの主な方法で配布されます。

### <a name="distributions"></a>分布

.NET Core は、「[.NET Core Getting Started](https://www.microsoft.com/net/core)」 (.NET Core の概要) ページでダウンロードできます。

- *Microsoft .NET Core* 配布には、CoreCLR ランタイム、関連付けられているライブラリ、コンソール アプリケーション ホスト、および `dotnet` アプリ ランチャーが含まれています。 これは [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) メタパッケージで記述されます。
- *Microsoft .NET Core SDK* 配布には、.NET Core と、NuGet パッケージの復元およびアプリのコンパイルとビルドのためのツール セットが含まれています。 

通常、.NET Core 開発を開始するには、最初に .NET Core SDK をインストールします。 追加の .NET Core (たとえばプレリリース版) ビルドをインストールすることもできます。

### <a name="packages"></a>パッケージ

- [.NET Core パッケージ](packages.md)には、.NET Core ランタイムおよびライブラリ (参照アセンブリおよび実装) が含まれています。 たとえば、[System.Net.Http](https://www.nuget.org/packages/System.Net.Http/) です。
- [.NET Core メタパッケージ](packages.md)は、バージョン管理されたライブラリ パッケージの適切なセットを参照することで、さまざまなレイヤーおよびアプリモデルを記述します。

## <a name="architecture"></a>アーキテクチャ

.NET Core は、クロスプラットフォーム .NET 実装です。 .NET Core に固有の主要なアーキテクチャの問題は、サポートされているプラットフォームでプラットフォーム固有の実装を提供することに関連します。

### <a name="environments"></a>環境

.NET Core は、Microsoft Windows、macOS、Linux でサポートされています。 Linux 上で Microsoft は、Red Hat Enterprise Linux (RHEL) および Debian 配布ファミリで実行されている .NET Core を主にサポートしています。

現在、.NET Core は X64 CPU をサポートしています。 Windows では、X86 もサポートされています。 ARM64 および ARM32 は進行中です。

「[.NET Core Roadmap](https://github.com/dotnet/core/blob/master/roadmap.md)」 (.NET Core ロードマップ) は、ワークロードと OS および CPU の環境サポートと計画に関する詳細情報を提供します。

他の企業やグループは、他のアプリの種類および環境に対して .NET Core をサポートする場合があります。

### <a name="designed-for-adaptability"></a>適応できる設計

.NET Core は、その他の .NET 製品と非常に似ているがユニークな製品としてビルドされています。 新しいワークロード用に新しいコンパイラ ツールチェーンにより、新しいプラットフォームへの広範な適応性を可能にするように設計されています。 進行中の複数の OS および CPU ポートがあり、さらに多くの OS に移植できます。 例として、[LLVM](http://llvm.org/) コンパイラによる .NET Core のネイティブ コンパイルの初期プロトタイプである、[LLILC](https://github.com/dotnet/llilc) プロジェクトがあります。

この製品は複数の部分に分割されており、さまざまなスケジュールで新しいプラットフォームにさまざまな部分を適応させることができます。 ランタイムとプラットフォーム固有の基本的なライブラリは、ユニットとして移植する必要があります。 プラットフォームに依存しないライブラリは、構造により、すべてのプラットフォームでそのまま機能します。 開発者の効率性を高めるために、プロジェクトではプラットフォーム固有の実装を低減する傾向にあり、その方向でアルゴリズムまたは API を完全または部分的に実装できる場合は、プラットフォームに依存しない C# コードが常に優先されます。

ユーザーから、複数のオペレーティング システムをサポートするには .NET Core をどのように実装すべきかという質問をよく受けます。 多いのは、個別の実装を行うのか、または[条件付きコンパイル](https://en.wikipedia.org/wiki/Conditional_compilation)を使用するのかという質問です。 どちらも正しいですが、条件付きコンパイルが特に好まれる傾向にあります。

次の図に示すように、 [CoreFX](https://github.com/dotnet/corefx) の大部分は、すべてのプラットフォーム間で共有されているプラットフォームに依存しないコードです。 プラットフォームに依存しないコードは、すべてのプラットフォームで使用される 1 つのポータブル アセンブリとして実装できます。

![CoreFX: プラットフォームごとのコードの行](../images/corefx-platforms-loc.png)

Windows 実装と Unix 実装はほぼ同じサイズです。 CoreFX は、[Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) などの Windows 専用の機能をいくつか実装しますが、Unix 専用の概念はまだ実装しないので、Windows の実装の方が大きくなります。 また、Linux 実装と macOS 実装の大部分は Unix 実装全体で共有されており、Linux 固有の実装と macOS 固有の実装はほぼ同じサイズです。


.NET Core には、プラットフォーム固有のライブラリとプラットフォームに依存しないライブラリが混在しています。 このパターンは次のいくつかの例に見られます。

- [CoreCLR](https://github.com/dotnet/coreclr) はプラットフォーム固有です。 C/C++ でビルドされるので、構造によりプラットフォーム固有です。
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) と [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) は、記憶域および暗号化 API が各 OS で大幅に異なるので、プラットフォーム固有です。 
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) と [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) は、データ構造上で作成および操作を行うので、プラットフォームに依存しません。

## <a name="comparisons-to-other-net-platforms"></a>その他の .NET プラットフォームとの比較

.NET Core のサイズとシェイプは、既存の .NET プラットフォームと比較するとよくわかります。 

### <a name="comparison-with-net-framework"></a>.NET Framework との比較

.NET プラットフォームは、最初に 2000 年に Microsoft によって発表され、進化してきました。 .NET Framework はその後 15 年以上にわたり、Microsoft によって製造される主要な .NET 製品となっています。 

.NET Core と .NET Framework の主な違いは、次のとおりです。 

- **アプリモデル** -- .NET Core は、すべての .NET Framework アプリモデルをサポートするわけではありません。その理由の 1 つは、それらの多くが WPF (DirectX の上にビルドされる) などの Windows テクノロジに基づいてビルドされることにあります。 コンソールおよび ASP.NET Core アプリモデルは、.NET Core と .NET Framework の両方でサポートされています。 
- **API** -- .NET Core には、.NET Framework と同じ API の多くが含まれており (ただし、数はそれよりも少ない)、異なるファクタリングを使用します (アセンブリ名が異なります。主要なケースでは型シェイプが異なります)。 現在、これらの違いにより、通常は .NET Core のポート ソースへの変更が必要となります。 .NET Core は [.NET 標準ライブラリ](../standard/library.md) API を実装します。この API は、時間の経過に伴って .NET Framework BCL API のより多くの部分を含めるようにサイズが増加します。
- **サブシステム** -- .NET Core は、より単純な実装とプログラミング モデルを目的として、.NET Framework 内のサブシステムのサブセットを実装します。 たとえば、コード アクセス セキュリティ (CAS) はサポートされていませんが、リフレクションはサポートされています。
- **プラットフォーム** -- .NET Framework は Windows と Windows Server をサポートしており、.NET Core は macOS と Linux もサポートしています。
- **オープン ソース** -- .NET Core はオープン ソースであり、[.NET Framework の読み取り専用のサブセット](https://github.com/microsoft/referencesource)はオープン ソースです。

.NET Core はユニークな製品で、.NET Framework およびその他の .NET プラットフォームとは大きな違いがあり、ソースまたはバイナリの共有技術を使用してコードを簡単に共有できます。 

### <a name="comparison-with-mono"></a>Mono との比較

[Mono](http://www.mono-project.com/) は、オリジナルのクロスプラットフォームおよび[オープン ソース](https://github.com/mono/mono)の .NET 実装であり、2004 年に登場しました。 .NET Framework のコミュニティの複製として考えることができます。 Mono プロジェクト チームは、互換性のある実装を提供するために、Microsoft によって発行されたオープン [.NET 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (特に ECMA 335) に依存していました。

.NET Core と .NET Mono の主な違いは、次のとおりです。

- **アプリモデル** -- Mono は、Xamarin 製品を介して .NET Framework アプリモデル (たとえば、Windows フォーム) のサブセットおよびいくつかの追加のアプリモデル (たとえば、[Xamarin.iOS](https://www.xamarin.com/platform)) をサポートしています。 .NET Core はこれらをサポートしていません。
- **API** -- Mono は、.NET Framework API の[大規模なサブセット](http://docs.go-mono.com/?link=root%3a%2fclasslib)をサポートしており、同じアセンブリ名およびファクタリングを使用します。
- **プラットフォーム** -- Mono は、さまざまなプラットフォームおよび CPU をサポートしています。
- **オープン ソース** --Mono と .NET Core は両方とも MIT ライセンスを使用しており、.NET Foundation プロジェクトです。
- **フォーカス** -- 近年、Mono はモバイル プラットフォームに重点を置いており、.NET Core はクラウド ワークロードを重視しています。

