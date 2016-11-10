---
title: ".NET 製品"
description: ".NET 製品"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 06/23/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 2e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: 90deb1903eea6ae1336326ca91f1e7863485dfd1

---

# <a name="net-products"></a>.NET 製品

.NET は、開発者向け製品を構築するためにとても柔軟で汎用的な仕組みを備えた、本質的にクロスプラットフォーム対応の[仕様](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)です。 デスクトップ、モバイル、クラウド、ゲーム、および IoT といった一般的なアプリケーション カテゴリのすべてに使用されます。

このドキュメントでは、微妙に異なる次の 2 つの用語が使用されています。

- ".NET 製品" - 1 つ以上のターゲット プラットフォーム向けにアプリをビルドできます。
- ".NET 実装" - 製品のベースとなる ".NET コード" を実行可能なランタイム、フレームワーク、およびツールの組み合わせです。

## <a name="product-categories"></a>製品カテゴリ

次の製品カテゴリのそれぞれに対して .NET 製品を利用できます。

### <a name="desktop"></a>デスクトップ

Windows や macOS 向けにデスクトップ アプリをビルドできます。

- [.NET Native](#net-native) を使用した [ユニバーサル Windows アプリ](https://developer.microsoft.com/windows)
- [.NET Framework](#net-framework) を使用した Windows 向けの [Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx)
- [.NET Framework](#net-framework) を使用した Windows 向けの [Windows フォーム](https://msdn.microsoft.com/library/dd30h2yb.aspx)
- [Xamarin](#xamarin-sdk) を使用した Cocoa for macOS
- [electron-edge](https://github.com/kexplo/electron-edge) を使用したクロスプラットフォーム デスクトップ向けの [Electron](http://electron.atom.io/)

### <a name="games"></a>ゲーム

さまざまなデスクトップ、モバイル、コンソール、および仮想/拡張現実デバイス向けにゲームをビルドできます。

- [Mono](#mono) を使用した [CRYENGINE](http://docs.cryengine.com/display/CEPROG/CE%23+Programming)
- [Mono](#mono) を使用した [MonoGame](http://www.monogame.net/documentation/?page=main)
- [Mono](#mono) を使用した [Unity](http://docs.unity3d.com/Manual/index.html)

### <a name="iot"></a>IoT

Raspberry Pi 2/3 などの Windows 10 IoT Core 向けに IoT アプリをビルドできます。

- [.NET Native](#net-native) を使用した [Windows 10 IoT Core](https://developer.microsoft.com/windows/iot)

### <a name="mobile"></a>携帯

iOS、Android、および Windows 向けにモバイル アプリをビルドできます。

- [Xamarin](#xamarin-sdk) を使用した iOS アプリ
- [Xamarin](#xamarin-sdk) を使用した Android アプリ
- [.NET Native](#net-native) を使用した[ユニバーサル Windows アプリ](https://developer.microsoft.com/windows)

### <a name="web-and-cloud"></a>Web とクラウド

Windows および Linux 向けに Web アプリやクラウド アプリをビルドできます。

- [.NET Framework](#net-framework) を使用した Windows 向けの [ASP.NET](http://www.asp.net/)
- [.NET Core](#net-core) を使用した Windows、macOS、および Linux 向けの [ASP.NET Core](http://docs.asp.net/)

## <a name="net-implementations"></a>.NET 実装

主要な市販およびオープン ソースの .NET 実装をアルファベット順に以下に示します。

### <a name="net-core"></a>.NET Core

.NET Core は、デバイス アプリ、Web アプリ、クラウド アプリ、および埋め込み/IoT アプリをビルドするために使用されます。 [オープン ソース](https://github.com/dotnet/core)でクロスプラット フォームに対応しており、Windows、macOS、および Linux をサポートします。 [ASP.NET Core](http://docs.asp.net/) は、最も一般的な .NET Core 向けワークロードです。 Web アプリや Web サービスをオンプレミスやクラウドの展開用にビルドするために使用できます。 また、.NET Core を使用して、ツール、ユーティリティ、およびクラウド ワーカー アプリをビルドできます。

- [.NET Core](../core/index.md) の詳細情報
- [ASP.NET Core](http://docs.asp.net/) の詳細情報
- [.NET Core のダウンロード](http://dot.net/core)

.NET Core の主な特徴を次に示します。

**クロスプラットフォーム** - .NET Core は、Linux、Windows、および macOS の 3 つのオペレーティング システム ファミリをサポートしています。 .NET Core アプリは、既定でクロスプラットフォーム対応になります。 サポートされている複数の OS で修正せずに動作するアプリやライブラリを作成することができます。

**オープン ソース** - [.NET Core](https://github.com/dotnet/core) は GitHub から入手することができ、[MIT](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT) および [Apache 2](https://github.com/dotnet/roslyn/blob/master/License.txt) ライセンスが適用されます (ライセンスの付与はコンポーネント単位です)。 ドキュメントは、[CC-BY](https://github.com/dotnet/docs/blob/master/license.txt) です。 また、.NET Core では、[.NET Core リリース ノート](https://github.com/dotnet/core/releases)に記載されているように、オープン ソース業界の依存関係セットが多数使用されています。 

**簡単に入手可能** - .NET Core は、特定の開発者のニーズに合わせて複数の形式で配布されています。 .NET Core を入手するには、[.NET Core SDK](https://dot.net/core) インストーラー (または zip) を使用するか、APT や Yum などの OS 固有のパッケージ マネージャーを使用することができます。 [公式の .NET Core Docker イメージ](https://hub.docker.com/r/microsoft/dotnet/)は、Docker Hub から入手できます。 さらに高度なレベルのフレームワーク ライブラリや、より大規模な .NET ライブラリ エコシステムは、[NuGet](http://www.nuget.org/) から入手できます。 

**モジュール型プラットフォーム** - .NET Core はモジュール型の設計で構築されており、アプリケーションには必要な .NET Core ライブラリと依存関係のみを含めることができます。 各アプリケーションで独自の .NET Core バージョンが選択されるため、共有コンポーネントの競合を回避することができます。 この手法は、Docker のようなコンテナー テクノロジを活用するソフトウェア開発のトレンドにマッチしています。

### <a name="net-framework"></a>.NET Framework

.NET Framework は、Windows および Windows Server 用のアプリをビルドするために使用されます。 Windows Presentation Framework (WPF) と Windows フォームを使用した機能豊富なユーザー インターフェイスを作成することができます。 また、.NET Framework は ASP.NET Web フォーム、ASP.NET MVC、および Windows Communication Framework (WCF) を使用するサーバー アプリのビルドもサポートしています。 Visual Studio には、.NET Framework 向けに豊富なデザイナー エクスペリエンスが用意されており、クライアントおよびサーバー用の両方のアプリを簡単にビルドできます。 Windows 用アプリの作成に最適な環境です。

- [.NET Framework](https://msdn.microsoft.com/library/w0x726c2.aspx) の詳細情報
- [.NET Framework のダウンロード](https://dot.net)

[Windows フォーム](https://msdn.microsoft.com/library/dd30h2yb.aspx)を使用すると、"フォーム オーバー データ" のデスクトップ UI を他のテクノロジよりも迅速に作成できます。 デザイナーを使用して UI や UI 以外のコントロールをドラッグ アンド ドロップで配置することができ、ほとんどの開発タスクが 1 つのジェスチャや概念モデルに簡素化されます。

[Windows Presentation Foundation (WPF)](https://msdn.microsoft.com/library/ms754130.aspx) では、[XAML](https://msdn.microsoft.com/library/ms752059.aspx) マークアップ言語を使用して UI を記述することで、コードと UI の問題が分離されます。 WPF は柔軟性の高い設計になっており、多くの場合、より複雑なユーザー モデルや洗練された外観が必要な UI の作成に使用されます。

[Windows Communication Foundation (WCF)](https://msdn.microsoft.com/library/ms731082.aspx) は、SOAP Web サービス用のライブラリ セットです。 WCF を使用して作成したサービスは、さまざまなデータ形式を使用して、サポートされているさまざまなプロトコル経由で通信でき、選択した任意のプロセスでホストすることができます。 その結果、サービスが特定のホスティング手法やアプローチに依存しないという WCF の主要な特徴の 1 つが実現されます。

[ASP.NET](http://www.asp.net/) は Web フレームワークです。 最新の高性能な Web アプリケーションの作成に使用される複数のコンポーネントで構成されています。 

- [ASP.NET Web フォーム](http://www.asp.net/web-forms)を使用すると、Web コントロールをドラッグ アンド ドロップできるデザイナーによって、"フォーム オーバー データ" UI を他のほとんどの Web テクノロジよりも迅速に作成することができます。 
- [ASP.NET MVC](http://www.asp.net/mvc) を使用すると、HTTP 層からユーザー インターフェイスに至るまで Web 全体のパイプラインをきめ細かく制御できます。 
- [ASP.NET Web API](http://www.asp.net/web-api) は REST サービスを作成するための規約ベースのフレームワークです。 
- [SignalR](http://www.asp.net/signalr) を使用すると、Web アプリケーションに [WebSocket](https://en.wikipedia.org/wiki/WebSocket) プロトコル経由でプッシュベースの通信を提供できます。

### <a name="net-native"></a>.NET Native

.NET Native は .NET Core 用のネイティブ ビルド ツールのセットです。 .NET Native は Ahead-of-Time (AOT) のツールチェーンであり、IL バイト コードをネイティブ マシン コードにコンパイルしてネイティブ アプリケーションを生成します。 そのため、生成されたバイナリは OS が直接実行することができ、JIT 処理やランタイムのコンパイルは発生しません。 これにより起動時のパフォーマンスが向上し、セキュリティ上の利点も得られます。

.NET Native は、主に .NET [ユニバーサル Windows プラットフォーム (UWP)](https://msdn.microsoft.com/library/windows/apps/dn726767.aspx) アプリケーションで使用されます。

### <a name="mono"></a>Mono

[Mono](http://www.mono-project.com/docs/about-mono/) は元々 [Mono プロジェクト](http://mono-project.com)のコミュニティから生まれたオープン ソースのクロスプラットフォーム対応 .NET 実装です。 現在はマイクロソフトが後援しています。 Mono は、.NET Framework のオープンなクロスプラットフォーム バージョンとして考えることができます。 その API は .NET Core ではなく .NET Framework の開発状況に従っています。

Mono は次のような複数のコンポーネントで構成されています。

**C# コンパイラ** - Mono の C# コンパイラは C# 6 のすべての機能に対応しています。

**Mono ランタイム** - このランタイムは ECMA 共通言語基盤 (CLI) を実装しています。 Just-in-Time (JIT) コンパイラ、Ahead-of-Time (AOT) コンパイラ、ライブラリ ローダー、ガベージ コレクター、スレッド システム、および相互運用性の機能が提供されます。

**基底クラス ライブラリ** - Mono プラットフォームには、アプリケーション構築の強固な基盤となる包括的な一連のクラスが用意されています。 これらのクラスは、マイクロソフトの .Net Framework クラスと互換性があります。

**Mono クラス ライブラリ** - Mono には、.NET Framework で提供される基底クラス ライブラリ以外にも多数のクラスが用意されています。 これらのクラスが提供する追加の機能は、特に Linux アプリケーションのビルドに役立ちます。 たとえば、Gtk+、Zip ファイル、LDAP、OpenGL、Cairo、POSIX などのクラスを利用できます。

### <a name="xamarin-sdk"></a>Xamarin SDK

[Xamarin SDK](http://open.xamarin.com) は、主に Apple と Google のエコシステムでネイティブのモバイル アプリやデバイス アプリをビルドするために使用されます。 Mono が基盤となっており、MIT ライセンスを使用するオープン ソースの製品です。 スマートフォンやタブレット、スマートウォッチ向けの iOS アプリや Android アプリをビルドするために使用できます。 [Xamarin.Forms](https://www.xamarin.com/forms) は、Apple、Google、および Windows アプリの間で再利用可能な UI を記述するための一般的な方法です。

- [Xamarin SDK](https://developer.xamarin.com/) の詳細情報
- [Xamarin のダウンロード](https://www.xamarin.com/platform)



<!--HONumber=Nov16_HO1-->


