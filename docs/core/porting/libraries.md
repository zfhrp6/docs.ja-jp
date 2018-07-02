---
title: .NET Core への移植 - ライブラリ
description: ライブラリ プロジェクトを .NET Framework から .NET Core に移植する方法を説明します。
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.openlocfilehash: 0f1d79623b4ece836732010e76a3c93fbbf8099f
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028046"
---
# <a name="porting-to-net-core---libraries"></a>.NET Core への移植 - ライブラリ

この記事では、ライブラリ コードを .NET Core に移植し、クロスプラットフォームで実行されるようにする方法について説明します。

## <a name="prerequisites"></a>必須コンポーネント

この記事では、以下を前提とします。

- Visual Studio 2017 以降を使用している。
  - それ以前のバージョンの Visual Studio では、.NET Core がサポートされていません。
- [推奨の移植プロセス](index.md)を理解している。
- [サード パーティの依存関係](third-party-deps.md)の問題が解決されている。

次のトピックの内容を理解している必要もあります。

[.NET Standard](~/docs/standard/net-standard.md)   
このトピックでは、すべての .NET 実装で使用可能にすることを目的とした、.NET API の正式な仕様について説明します。

[パッケージ、メタパッケージ、フレームワーク](~/docs/core/packages.md)   
この記事では、.NET Core でのパッケージの定義と使用について説明すると共に、複数の .NET 実装で実行されるコードがパッケージでどのようにサポートされるかについて説明します。

[クロス プラットフォーム ツールによるライブラリの作成](~/docs/core/tutorials/libraries.md)   
このトピックでは、クロスプラットフォーム CLI ツールを使用して .NET 用ライブラリを作成する方法について説明します。

[.NET Core の *csproj* 形式に追加されたもの](~/docs/core/tools/csproj.md)   
この記事では、*csproj* および MSBuild への移行に伴ってプロジェクト ファイルに追加された変更について説明します。

[.NET Core への移植 - サード パーティの依存関係の分析](~/docs/core/porting/third-party-deps.md)   
このトピックでは、サード パーティの依存関係の移植性と、NuGet パッケージの依存関係が .NET Core で機能しない場合の対処方法について説明します。

## <a name="net-framework-technologies-unavailable-on-net-core"></a>.NET Core で使用できない .NET Framework テクノロジ

.NET Framework ライブラリで使用できるテクノロジの中には、.NET Core で使用できないものがあります。たとえば、AppDomain、リモート処理、コード アクセス セキュリティ (CAS)、セキュリティ透過性などです。 ライブラリがこれらのテクノロジの 1 つ以上に依存する場合、以下に示す代替方法を検討してください。 API の互換性の詳細については、CoreFX チームが GitHub で提供する[動作の変更/互換性の破棄と廃止/レガシ API の一覧](https://github.com/dotnet/corefx/wiki/ApiCompat)をご覧ください。

API またはテクノロジが現在実装されていないからといって、意図的にサポートされていないわけではありません。 GitHub の [dotnet/corefx リポジトリの問題](https://github.com/dotnet/corefx/issues)に問題点を挙げて、特定の API やテクノロジについて質問してください。 [問題内の移植に関する要求](https://github.com/dotnet/corefx/labels/port-to-core)には、`port-to-core` のラベルが付いています。

### <a name="appdomains"></a>AppDomain

AppDomain はアプリを互いに分離します。 AppDomain ではランタイム サポートが必要で、通常は非常に高額です。 .NET Core には実装されていません。 将来この機能が追加される予定はありません。 コードの分離には、代わりの方法として、プロセスの分離やコンテナーの利用をお勧めします。 アセンブリの動的読み込みには、新しい <xref:System.Runtime.Loader.AssemblyLoadContext> クラスをお勧めします。

.NET Framework からのコードの移行を簡単にするために、.NET Core の <xref:System.AppDomain> API サーフェスの一部を公開しています。 API のなかには、正常に機能するもの (<xref:System.AppDomain.UnhandledException?displayProperty=nameWithType> など)、処理を行わないメンバー (<xref:System.AppDomain.SetCachePath%2A> など)、<xref:System.PlatformNotSupportedException> をスローするもの (<xref:System.AppDomain.CreateDomain%2A> など) があります。 [dotnet/corefx GitHub リポジトリ](https://github.com/dotnet/corefx)の[ `System.AppDomain` 参照ソース](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs)に照らして使用する種類を確認し、実装バージョンに合ったブランチを選択してください。

### <a name="remoting"></a>リモート処理

.NET リモート処理は、問題のあるアーキテクチャであると判断されました。 AppDomain 間の通信で使用されていますが、今後はサポートされなくなります。 また、リモート処理にはランタイム サポートが必要で、維持するのに高いコストがかかります。 これらの理由から、.NET リモート処理は .NET Core でサポートされておらず、また将来サポートが追加される予定もありません。

プロセス間の通信では、リモート処理に代わる方法として、<xref:System.IO.Pipes> または <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> クラスなどのプロセス間通信 (IPC) メカニズムを検討してください。

マシン間では、代替方法としてネットワーク ベースのソリューションを使用してください。 可能であれば、HTTP などのオーバーヘッドの少ないプレーンテキストのプロトコルを使用してください。 この場合、ASP.NET Core で使用される Web サーバーの [Kestrel Web Server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel) も選択できます。 また、ネットワーク ベースのマシン間のシナリオとして、<xref:System.Net.Sockets> の使用も検討してください。 その他のオプションについては、[.NET オープン ソース開発者プロジェクト: メッセージング](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging)に関する記事をご覧ください。

### <a name="code-access-security-cas"></a>コード アクセス セキュリティ (CAS)

サンド ボックスは、マネージド アプリケーションやライブラリが使用または実行するリソースの制限を、ランタイムまたはフレームワークに依存しています。これは [.NET Framework ではサポートされていない](~/docs/framework/misc/code-access-security.md)ため、.NET Core でもサポートされていません。 .NET Framework やランタイムでは、特権の昇格が発生するケースが多すぎるため、このまま CAS をセキュリティ境界と見なすことはできないと考えています。 さらに、CAS は実装が複雑化しており、その使用を予定していないアプリケーションでは、多くの場合で正確性のパフォーマンスに影響します。

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最低限の特権セットでプロセスを実行します。

### <a name="security-transparency"></a>セキュリティ透過性

CAS と同様に、セキュリティ透過性を利用すると、サンドボックス コードをセキュリティ クリティカルなコードから宣言的に分離できますが、[現在はセキュリティ境界としてはサポートされていません](~/docs/framework/misc/security-transparent-code.md)。 この機能は、Silverlight で頻繁に使用されます。 

仮想化、コンテナー、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最低限の特権セットでプロセスを実行します。

## <a name="converting-a-pcl-project"></a>PCL プロジェクトの変換

Visual Studio 2017 でライブラリを読み込み、次の手順を行うことで、PCL プロジェクトのターゲットを .NET Standard に変更できます。

1. プロジェクト ファイルを右クリックし、**[プロパティ]** を選択します。
1. **[ライブラリ]** から、**[ターゲットの .NET Platform Standard]** を選択します。

パッケージで NuGet 3.0 がサポートされている場合、プロジェクトは .NET Standard に再ターゲット設定します。

パッケージで NuGet 3.0 がサポートされていない場合、Visual Studio で、現在のパッケージをアンインストールするように促すダイアログが表示されます。 この通知が表示される場合は、次の手順を実行します。

1. プロジェクトを右クリックし、**[NuGet パッケージの管理]** を選択します。
1. プロジェクトのパッケージをメモしておきます。
1. パッケージを 1 つずつアンインストールします。
1. アンインストール プロセスを完了するには、Visual Studio を再起動しなくてはならない場合があります。 その場合、**[NuGet パッケージ マネージャー]** ウィンドウに **[再起動]** ボタンが表示されます。
1. プロジェクトが再度読み込まれると、.NET Standard がターゲット設定されます。 アンインストールが必要なパッケージを追加します。

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>.NET Framework コードのターゲットを .NET Framework 4.6.2 に変更する

コードのターゲットが .NET Framework 4.6.2 でない場合、.NET Framework 4.6.2 に再ターゲット設定することをお勧めします。 ターゲット設定することで、.NET Standard が既存の API をサポートしていない場合に、最新の代替 API を使用できるようになります。

移植する Visual Studio の各プロジェクトで、次の手順を実行します。

1. プロジェクトを右クリックし、[プロパティ] を選択します。
1. **[対象とする Framework]** ボックスの一覧で、**[.NET Framework 4.6.2]** を選択します。
1. プロジェクトを再コンパイルします。

プロジェクトのターゲットが .NET Framework 4.6.2 になったため、コード移植のベースとして .NET Framework 4.6.2 を使用できます。

## <a name="determining-the-portability-of-your-code"></a>コードの移植性を判別する

次の手順では、API Portability Analyzer (ApiPort) を実行して、分析用の移植性レポートを生成します。

[API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) を理解し、.NET Core をターゲットとする移植性レポートを生成する方法を理解している必要があります。 その方法は、ニーズと個人の好みによって変わります。 以下に、異なるアプローチをいくつか示します。 コードの構成内容によっては、これらのアプローチの手順を組み合わせて使用していることに気付くかもしれません。

### <a name="dealing-primarily-with-the-compiler"></a>主にコンパイラを使用して対処する

このアプローチは、小さなプロジェクト、つまり多くの .NET Framework API を使用しないプロジェクトにお勧めです。 このアプローチは単純です。

1. 必要に応じてプロジェクトで ApiPort を実行します。 ApiPort を実行すると、レポートから対応が必要となる問題についての情報を得られます。
1. すべてのコードを新しい .NET Core プロジェクトにコピーします。
1. 移植性に関するレポート (生成されている場合) を参照しながら、プロジェクトが完全にコンパイルされるまでコンパイラ エラーを解決します。

これは非体系的なアプローチですが、多くの場合、コード中心のアプローチが問題を迅速に解決します。また、これは小規模なプロジェクトやライブラリに最適なアプローチかもしれません。 特に、データ モデルのみが含まれるプロジェクトにはこのアプローチが最適です。

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>移植性の問題が解決されるまで .NET Framework を使い続ける

このアプローチは、すべてのプロセスでコンパイルできるコードを作成したい場合にお勧めです。 アプローチは次のとおりです。

1. プロジェクトで ApiPort を実行します。
1. 移植可能な別の API を使用して問題に対処します。
1. 直接の代替方法を使用できない領域をすべて書き留めます。
1. 新しい .NET Core プロジェクトにコピーしても問題ないことが確認できるまで、移植するすべてのプロジェクトに対して前の手順を繰り返します。
1. コードを新しい .NET Core プロジェクトにコピーします。
1. 直接の代替手段がないと書き留めた問題に対処します。

この慎重なアプローチは、コンパイラ エラーに対処するだけの方法よりも体系的ですが、それでも比較的コード中心であり、コンパイルできるコードが常にあるという利点があります。 別の API を使用するだけでは解決できなかった問題を解決する方法は、大きく異なります。 プロジェクトによっては、次のアプローチのように、より包括的な計画を開発する必要があります。

### <a name="developing-a-comprehensive-plan-of-attack"></a>包括的な計画を新たに作成する

このアプローチは、.NET Core をサポートするために、コードの再構築や特定範囲の完全な書き換えが必要になる可能性があるような、大規模で複雑なプロジェクトにお勧めです。 アプローチは次のとおりです。

1. プロジェクトで ApiPort を実行します。
1. 移植できない性質のものが使用されている箇所と、それが移植性全体に与える影響を把握します。
   - 種類の性質を理解します。 数は少なくても使用頻度は高いですか。 数は多くても使用頻度は低いですか。 コードで集中して使用されていますか、それともあちこちで使用されていますか。
   - 移植できないコードの分離は簡単で、効果的に処理できますか。
   - コードをリファクタリングする必要はありますか。
   - 移植可能ではない種類の場合、同じ作業を実行できる代替 API はありますか。 たとえば、<xref:System.Net.WebClient> クラスを使用している場合は、代わりに <xref:System.Net.Http.HttpClient> クラスを使用できます。
   - 一時的な置き換えでない場合でも、作業を完了させるのに使用できる、移植可能な API が別にありますか。 たとえば、<xref:System.Xml.Schema.XmlSchema> を使用して XML を解析しているが、XML スキーマ検出が不要な場合、<xref:System.Xml.Linq> API を使用して API に依存しない解析を独自に実装できます。
1. 移植が困難なアセンブリがある場合、.NET Framework を今すぐ止める価値はあるでしょうか。 次の点を考慮することをお勧めします。
   - .NET Framework または Windows 固有の機能への依存度が高いために、.NET Core との互換性がない機能がライブラリにあるとします。 ただちにその機能をあきらめ、機能を移植できるリソースが利用できるようになるまで、機能の少ない .NET Core バージョンのライブラリを一時的にリリースするのがよいでしょうか。
   - リファクタリングが有効でしょうか。
1. 使用できない .NET Framework API の代わりになる実装を開発することは理にかなっていますか。
   [.NET Framework の参照ソース](https://github.com/Microsoft/referencesource)のコードのコピー、変更、および使用も検討できます。 この参照ソース コードは [MIT ライセンス](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)の下で使用が許可されているため、このソースをコードの基盤として、かなり自由に使用できます。 ただし、コードには Microsoft への帰属を適切に示してください。
1. プロジェクトごとにこのプロセスを繰り返します。
 
コードベースのサイズによっては、分析フェーズに時間がかかる場合があります。 このフェーズに時間を割き、必要な変更の範囲を完全に把握してから計画を立てることで、長期的には多くの時間を節約できます。特に、コードベースが複雑な場合には有効です。

コードベースの大幅な変更が必要な計画になる可能性がありますが、ターゲット設定は .NET Framework 4.6.2 です。そのため、これは前のアプローチよりも体系化されたバージョンです。 計画の実施方法は、コードベースによって異なります。

### <a name="mixing-approaches"></a>混合アプローチ

多くの場合は、プロジェクトごとに、前述のアプローチを混合して利用します。 自分とコードベースにとって最も有用な処理を実行するようにします。

## <a name="porting-your-tests"></a>テストを移植する

コードを移植したときにすべての機能が動作することを確認するには、コードを .NET Core に移植してテストすることをお勧めします。 このテストを行うには、.NET Core 用のテストを構築して実行するためのテスト フレームワークを使用する必要があります。 現在のところ、次の 3 つの選択肢があります。

- [xUnit](https://xunit.github.io/)
  * [はじめに](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [MSTest プロジェクトを xUnit に変換するツール](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [はじめに](https://github.com/nunit/docs/wiki/Installation)
  * [MSTest から NUnit への移行に関するブログ投稿](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>移植について推奨されるアプローチ

最終的に、移植作業は .NET Framework コードの構成内容に大きく左右されます。 コードを移植するのに良い方法は、コードの基本コンポーネントであるライブラリの*ベース*から始めることです。 ベースは、その他すべてが直接または間接的に使用するデータ モデル、または他の基本クラスやメソッドの場合があります。

1. 移植対象のライブラリのレイヤーをテストするテスト プロジェクトを移植します。
1. ライブラリのベースを新しい .NET Core プロジェクトにコピーし、サポートする .NET Standard のバージョンを選択します。
1. 必要に応じてコードを変更し、コンパイルします。 多くの場合、NuGet パッケージの依存関係を *csproj* ファイルに追加する必要があります。
1. テストを実行し、必要な調整を行います。
1. 次のコード レイヤーを選択して移植し、前の手順を繰り返します。

ライブラリのベースから開始してベースから外側に向かい、必要に応じて各レイヤーをテストする場合、移植は、問題が一度でコードの 1 レイヤーに分離される体系的なプロセスになります。
