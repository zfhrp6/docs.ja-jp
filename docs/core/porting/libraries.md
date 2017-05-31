---
title: ".NET Core への移植 - ライブラリ"
description: ".NET Core への移植 - ライブラリ"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: a0fd860d-d6b6-4659-b325-8a6e6f5fa4a1
ms.translationtype: Human Translation
ms.sourcegitcommit: 50e128137fde445f64e10cf7c2a1ee5fdecb34e6
ms.openlocfilehash: 883745ca26a9c0d4bd1db805da603aa6e2c41972
ms.contentlocale: ja-jp
ms.lasthandoff: 05/01/2017

---

# <a name="porting-to-net-core---libraries"></a>.NET Core への移植 - ライブラリ

.NET Core 1.0 がリリースされ、既存のライブラリをコードを移植してクロスプラットフォームを実行できるようになりました。 この記事では、.NET Standard Library、使用できないテクノロジ、.NET Core 1.0 で使用できる少ない数の API の考慮、.NET Core SDK Preview 2 に付属するツールの使用方法、推奨されるコードの移植方法について説明します。

移植は時間がかかる可能性がある作業です。コードベースが大きいときは特にそうです。 実際のコードに合わせ、このガイダンスを採用するようにしてください。 すべてのコードベースに同じものはないので、この記事では柔軟な方法でガイダンスを構成するように心がけていますが、必要に応じて所定のガイダンスから逸脱してもかまいません。

## <a name="prerequisites"></a>必要条件

この記事では、Windows で Visual Studio 2017 以降を使用していると想定しています。 旧バージョンの Visual Studio では、.NET Core コードの構築に必要な機能の一部を使用できません。

また、この記事では、[推奨される移植プロセス](index.md)を理解し、[サードパーティの依存関係に関する問題を解決した](third-party-deps.md)と想定しています。

## <a name="targeting-the-net-standard-library"></a>.NET Standard Library のターゲット設定

.NET Core 用のクロスプラットフォーム ライブラリを構築する最適な方法は、[.NET Standard Library のターゲット設定](../../standard/library.md)です。 .NET Standard Library は、すべての .NET ランタイム上で使用できることを意図した .NET API の正式な仕様です。 このライブラリは .NET Core ランタイムでサポートされています。

つまり、使用できる API とサポートできるプラットフォームとのトレードオフを考え、目的のトレードオフに最適な .NET Platform Standard のバージョンを選択する必要があります。

現時点で、.NET Standard には 1.0 から 1.6 まで 7 つのバージョンがあります。 新しいバージョンを選択すると、使用できる API は多くなりますが、動作するターゲットは少なくなります。 古いバージョンを選択すると、動作するターゲットは多くなりますが、使用できる API は少なくなります。

参考までに、各 .NET Standard バージョンと、それぞれの実行領域の一覧を次に示します。

| プラットフォーム名 | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Mono/Xamarin プラットフォーム||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|ユニバーサル Windows プラットフォーム|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

**古いバージョンをターゲットとするプロジェクトは、新しいバージョンをターゲットとするプロジェクトを参照できない**、という点を把握することが重要です。 たとえば、.NET Platform Standard バージョン 1.2 をターゲットとするプロジェクトは、.NET Platform Standard バージョン 1.3 以降をターゲットとするプロジェクトを参照できません。 プロジェクトは古いバージョンを**参照できる**ので、.NET Platform Standard 1.3 をターゲットとするプロジェクトは、.NET Platform Standard 1.2 以前をターゲットとするプロジェクトを参照できます。

可能な限り古い .NET Standard バージョンを選択し、プロジェクト全体でそれを使用することをお勧めします。

詳細については、「[.NET Platform Standard Library](../../standard/library.md)」を参照してください。

## <a name="key-technologies-not-yet-available-on-the-net-standard-or-net-core"></a>.NET Standard または .NET Core でまだ使用できない主要テクノロジ

現在は .NET Core で使用できず、.NET Framework では使用できるテクノロジがあります。 以下の各サブセクションは、そのような各テクノロジに対応しています。 代替方法も挙げていますので、可能な場合は採用してください。

### <a name="app-domains"></a>アプリ ドメイン

AppDomains は、.NET Framework でさまざまな目的に使用されます。 コードの分離のためには、代替方法としてプロセスやコンテナーを別にすることが推奨されます。 アセンブリの動的読み込みには、新しい @System.Runtime.Loader.AssemblyLoadContext クラスが推奨されます。

### <a name="remoting"></a>リモート処理

プロセス間の通信のためには、[パイプ](https://docs.microsoft.com/dotnet/core/api/system.io.pipes)、[メモリ マップ ファイル](https://docs.microsoft.com/dotnet/core/api/system.io.memorymappedfiles.memorymappedfile)など、プロセス間通信 (IPC) メカニズムをローミングの代替方法として使用できます。

マシン間には、ネットワーク ベースのソリューションを代替方法として使用できます。できれば、HTTP など、オーバーヘッドの少ないプレーン テキスト プロトコルが推奨されます。 この場合、ASP.NET Core で使用される Web サーバーである [KestrelHttpServer](https://github.com/aspnet/KestrelHttpServer) も選択できます。 [Castle.Core](https://github.com/castleproject/Core) 経由のリモート プロキシ生成も、1 つの選択肢として考えられます。

### <a name="binary-serialization"></a>バイナリ シリアル化

バイナリ シリアル化の代替方法として、さまざまなシリアル化テクノロジを選択できます。 形式とフットプリントの目標に合わせて、いずれかのテクノロジを選択してください。 主に次の選択肢に人気があります。

* [JSON.NET](http://www.newtonsoft.com/json) (JSON 向け)
* @System.Runtime.Serialization.DataContractSerializer (XML および JSON 向け)
* @System.Xml.Serialization.XmlSerializer (XML 向け)
* [protobuf-net](https://github.com/mgravell/protobuf-net) (Protocol Buffers 向け)

リンクされているリソースを参照して利点を確認し、実際のニーズに合わせて選択してください。 他にも多数のシリアル化形式とテクノロジがあり、その多くはオープン ソースです。

### <a name="sandboxes"></a>サンドボックス

サンドボックスの代替方法として、ユーザー アカウントなど、オペレーティング システムが提供するセキュリティ境界を使用して、最低限の特権セットでプロセスを実行します。

## <a name="overview-of-projectjson"></a>`project.json` の概要

[project.json プロジェクト モデル](../tools/project-json.md)は、.NET Core SDK 1.0 Preview 2 に付属しているプロジェクト モデルです。 このプロジェクト モデルには、次のように、すぐに利用したいような利点があります。

* 単純なマルチターゲットで、ターゲット固有のアセンブリを 1 つのビルドから生成できる。
* プロジェクトのビルドで NuGet パッケージを簡単に生成できる。
* プロジェクト ファイル内のファイルを列挙する必要がない。
* NuGet パッケージの依存関係とプロジェクト間の依存関係の統一。

> `project.json` は最終的に廃止される予定ですが、現在は .NET Standard でのライブラリの構築に使用できます。

### <a name="the-project-file-projectjson"></a>プロジェクト ファイル: `project.json`

.NET Core プロジェクトは、`project.json` ファイルを含むディレクトリで定義されています。 このファイルには、パッケージの依存関係、コンパイラ構成、ランタイム構成など、プロジェクトのさまざまな側面が宣言されています。

`dotnet restore` コマンドは、このプロジェクト ファイルを読み取り、プロジェクトのすべての依存関係を復元し、`project.lock.json` ファイルを生成します。 このファイルには、ビルド システムがプロジェクトのビルドに必要なすべての情報が含まれています。

`project.json` ファイルの詳細については、[project.json リファレンス](../tools/project-json.md)を参照してください。

### <a name="the-solution-file-globaljson"></a>ソリューション ファイル: `global.json`

`global.json` ファイルは、複数のプロジェクトがあるソリューションに含まれているオプションのファイルです。 通常、プロジェクト セットのルート ディレクトリにあります。 ビルド システムに対して、プロジェクトが含まれる可能性がある複数のサブディレクトリについて通知するために、このファイルが使用されます。 このファイルは、複数のプロジェクトで構成される大規模なシステム向けです。

たとえば、次のように、コードを最上位の `/src` フォルダーや `/test` フォルダーに整理することができます。

```json
{
    "projects":[ "src", "test" ]
}
```

`/src` と `/test` 内のサブフォルダー以下に、複数の `project.json` ファイルを保存することができます。

### <a name="how-to-multitarget-with-projectjson"></a>`project.json` でマルチターゲットを設定する方法

多くのライブラリは、できるだけ対象が広くなるようにマルチターゲットを設定しています。 .NET Core では、マルチターゲット設定は "一流の市民" です。つまり、1 つのビルドでプラットフォーム固有の複数のアセンブリを簡単に生成できます。

マルチターゲット設定は、正しいターゲット フレームワーク モニカー (TFM) を `project.json` ファイルに追加するだけの簡単な操作です。その際に、各ターゲット (`dependencies` for .NET Core、`frameworkAssemblies` for .NET Framework) に合わせて正しい依存関係を使用し、必要に応じて `#if` ディレクティブを使用して、プラットフォーム固有の API 用法に合わせた条件付きでソース コードをコンパイルします。

たとえば、いくつかのネットワーク操作を実行するライブラリを構築し、このライブラリでは、すべての .NET Framework バージョン、ポータブル クラス ライブラリ (PCL) プロファイル、.NET Core 上で動作することを想定します。 .NET Core と .NET Framework 4.5 以降のターゲットの場合、`System.Net.Http` ライブラリと `async`/`await` を使用できます。 ただし、以前のバージョンの .NET Framework では、これらの API を使用できません。

次のサンプル `frameworks` セクションは、.NET Framework バージョン 2.0、3.5、4.0、4.5、および .NET Standard 1.6 をターゲットにする `project.json` 向けです。

```javascript
{
    "frameworks":{
        "net20":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net35":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net40":{
            "frameworkAssemblies":{
                "System.Net":""
            }
        },
        "net45":{
            "frameworkAssemblies":{
                "System.Net.Http":"",
                "System.Threading.Tasks":""
            }
        },
        ".NETPortable,Version=v4.5,Profile=Profile259": {
            "buildOptions": {
                "define": [ "PORTABLE" ]
             },
             "frameworkAssemblies":{
                 "mscorlib":"",
                 "System":"",
                 "System.Core":"",
                 "System.Net.Http":""
             }
        },
        "netstandard16":{
            "dependencies":{
                "NETStandard.Library":"1.6.0",
                "System.Net.Http":"4.0.1",
                "System.Threading.Tasks":"4.0.11"
            }
        },
    }
}
```

PCL ターゲットは特殊である点に注意してください。PCL ターゲットでは、コンパイラに認識させるビルド定義を指定する必要があります。また、`mscorlib` を含め、使用するすべてのアセンブリを指定する必要があります。

ソース コードには、次のように依存関係を使用できます。

```csharp
#if (NET20 || NET35 || NET40 || PORTABLE)
using System.Net;
#else
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

すべての .NET Framework と .NET Standard ターゲットには、コンパイラから認識される名前があります。

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

前述のように、PCL をターゲット設定している場合、コンパイラに理解させるビルド定義を指定する必要があります。 コンパイラが使用できる既定の定義はありません。

### <a name="using-projectjson-in-visual-studio"></a>Visual Studio で `project.json` を使用する

Visual Studio で `project.json` を使用する場合、2 つの選択肢があります。

1. 新しい xproj プロジェクトの種類。
2. .NET Standard をサポートするようにターゲットを再設定した PCL プロジェクト。

それぞれに利点と欠点があります。

#### <a name="when-to-pick-an-xproj-project"></a>Xproj プロジェクトを選択する場合

Visual Studio の新しい Xproj プロジェクト システムでは、`project.json` ベースのプロジェクト モデルの機能を利用して、既存のプロジェクトの種類に対して、複数のアセンブリをビルドしてシームレスにマルチターゲットを設定する機能と、ビルド時に NuGet パッケージを直接生成する機能という、主に 2 つの機能を提供できます。

ただし、次のように、一部の機能を使用できなくなる可能性があります。

- F# または Visual Basic のサポート
- リソース文字列がローカライズされたサテライト アセンブリを生成する
- ファイルシステム上の `.dll` ファイルを直接参照する
- 参照マネージャーの csproj ベースのプロジェクトを参照する機能 (ただし、`.dll` ファイルが直接サポートされているかどうかによります)

プロジェクトのニーズが比較的少なく、xproj の新しい機能を利用できる場合は、これをプロジェクト システムとして選択することをお勧めします。 この操作は、次のように Visual Studio で行うことができます。

1. この操作には、Visual Studio 2015 以降を使用してください。
2. [ファイル]、[新しいプロジェクト] の順に選択します。
3. Visual C# で [.NET Core] を選択します。
4. [クラス ライブラリ (.NET Core)] テンプレートを選択します。 

#### <a name="when-to-pick-a-pcl-project"></a>PCL プロジェクトを選択する場合

Visual Studio の従来のプロジェクト システムでは、.NET Core をターゲット設定することができます。ターゲット設定するには、ポータブル クラス ライブラリ (PCL) を作成し、プロジェクト構成ダイアログで [.NET Core] を選択します。 次に、.NET Standard に基づくようにプロジェクトのターゲットを再設定する必要があります。

1. Visual Studio でプロジェクト ファイルを右クリックし、[プロパティ] を選択します。
2. [ビルド] で 「Convert to .NET Standard」 (.NET Standard に変換) を選択します。

より高度なプロジェクト システムが必要な場合、これを選択することをお勧めします。 `xproj` プロジェクト システムなどのプラットフォーム固有のアセンブリを生成してマルチターゲットを設定する場合、「[How to Make Portable Class Libraries Work for You](https://blogs.msdn.microsoft.com/dsplaisted/2012/08/27/how-to-make-portable-class-libraries-work-for-you/)」(ポータブル クラス ライブラリを活用する方法) の説明を参照して、"おとり" の PCL を作成する必要があります。

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>.NET Framework コードのターゲットを .NET Framework 4.6.2 に変更する

コードのターゲットが .NET Framework 4.6.2 ではない場合は、ターゲット設定することをお勧めします。 ターゲット設定することで、.NET Standard が既存の API をサポートできない場合に、最新の代替 API を使用できるようになります。

移植する Visual Studio の各プロジェクトで、次の手順を実行します。

1. プロジェクトを右クリックし、[プロパティ] を選択します。
2. [対象とする Framework] ボックスの一覧で、[.NET Framework 4.6.2] を選択します。
3. プロジェクトを再コンパイルします。

以上です。 プロジェクトのターゲットは .NET Framework 4.6.2 になったので、コード移植のベースとして .NET Framework 4.6.2 を使用できます。

## <a name="determining-the-portability-of-your-code"></a>コードの移植性を判断する

次の手順は、API Portability Analyzer (ApiPort) を実行して、移植性レポートを生成することです。このレポートで分析を始めることができます。

[API Portability ツール (ApiPort)](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/) を理解し、.NET Core のターゲット設定のために移植性レポートを生成できるようになる必要があります。 その方法は、ニーズと個人の好みによって変わります。 次に、いくつかのアプローチを紹介します。実際のコードの構築方法に応じて、各アプローチを組み合わせることもできます。

### <a name="dealing-primarily-with-the-compiler"></a>主にコンパイラに対処する

このアプローチは、小さなプロジェクト、つまり多くの .NET Framework API を使用しないプロジェクトにお勧めです。 このアプローチはとても単純です。

1. 必要に応じてプロジェクトで ApiPort を実行します。
2. ApiPort が実行されていた場合は、レポートの概要を確認します。
3. すべてのコードを新しい .NET Core プロジェクトにコピーします。
4. コンパイルできるまでコンパイラ エラーに対応します。必要に応じて移植性レポートを参照します。
5. 必要に応じて繰り返します。

このアプローチはあまり体系化されていませんが、コード中心のアプローチは問題を迅速に解決できる可能性があります。また、小規模なプロジェクトやライブラリには最適なアプローチかもしれません。 特に、データ モデルのみが含まれるプロジェクトには最適です。

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>移植性の問題が解決されるまで .NET Framework を使い続ける

このアプローチは、プロセス全体で、コンパイルできるコードを持っている方を好む場合にお勧めです。 アプローチは次のとおりです。

1. プロジェクトで ApiPort を実行します。
2. 移植可能な別の API を使用して問題に対処します。
3. 代替の API を直接使用できない領域をメモしておきます。
4. .NET Core プロジェクトにコピーしても問題ないことが確認できるまで、移植するすべてのプロジェクトに対して手順 1 から 3 を繰り返します。
5. コードを新しい .NET Core プロジェクトにコピーします。
6. メモしておいた問題があれば解決します。

この慎重なアプローチは、コンパイラ エラーに対処するだけの方法よりも体系的ですが、それでも比較的にはコード中心であり、コンパイルできるコードが常にあるという利点があります。 別の API を使用するだけでは解決できない問題を解決する方法は、問題によって大きく異なります。 プロジェクトによっては、次のアプローチのように、より包括的な計画を開発する必要があります。

### <a name="developing-a-comprehensive-plan-of-attack"></a>攻撃に対する包括的な計画を開発する

このアプローチは、.NET Core をサポートするためにコードの再構築や特定領域の書き換えが必要になる可能性がある、大規模で複雑なプロジェクトにお勧めです。 アプローチは次のとおりです。

1. プロジェクトで ApiPort を実行します。
2. コードで移植できない種類が使用されている場所と、全体的な移植性に対する影響を把握します。

   a.  種類の性質を理解します。 数は少なくても頻繁に使用されていますか。 数は多くても使用頻度は低いですか。 コードで集中して使用されていますか、それともあちこちで使用されていますか。
   
   b.  移植可能ではないコードを分離することは簡単なので、簡単に処理できますか。
   
   c. コードをリファクタリングする必要はありますか。
   
   d. 移植可能ではない種類の場合、同じ作業を実行できる代替 API はありますか。 たとえば、`WebClient` クラスを使用している場合は、代わりに `HttpClient` クラスを使用できます。
   
   e. 当座の代替 API であっても、利用できる別の移植可能な API で作業を達成できますか。 たとえば、`XmlSchema` を使用して XML を解析し、XML スキーマの検出は必要ない場合、`System.Linq.Xml` API を使用し、データを手動解析することができます。

3. 移植が困難なアセンブリがある場合、.NET Framework を今すぐ止める価値はあるでしょうか。 次の点を考慮することをお勧めします。

   a.  .NET Framework または Windows 固有の機能に依存している部分が多いため、.NET Core と互換性がない機能がライブラリにいくつかあるとします。 今すぐその機能をあきらめて、しばらくの間、機能が少ない .NET Core バージョンのライブラリをリリースする価値はあるでしょうか。
   
   b.  リファクタリングが有効な場合ですか。
   
4. 使用できない .NET Framework API の代わりになる実装を開発することは理にかなっていますか。

   [.NET Framework のリファレンス ソース](https://github.com/Microsoft/referencesource)のコードをコピー、変更、および使用することもできます。 [MIT ライセンス](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)下でライセンスが付与されるので、高い自由度でこのような操作を行うことができます。 ただし、コードで Microsoft への帰属を適切に指定してください。
   
5. プロジェクトごとにこのプロセスを繰り返します。
6. 計画を作成したら、その計画を実行します。
 
コードベースのサイズに応じては、分析フェーズに時間がかかる可能性があります。 このフェーズに時間を使って、必要な変更の範囲を完全に把握し、計画を作成することで、長期的には多くの時間を節約できます。特に、複雑なコードベースであるほど、お勧めします。

コードベースの大幅な変更が必要な計画になる可能性がありますが、ターゲット設定は .NET Framework 4.6.2 です。そのため、これは前のアプローチよりも体系化されたバージョンです。 計画の取り組み方法は、コードベースによって異なります。

### <a name="mixing-approaches"></a>混合アプローチ

多くの場合は、プロジェクトごとに、前述のアプローチを混合して利用します。 自分とコードベースにとって最も有用な処理を実行するようにします。

## <a name="porting-your-tests"></a>テストを移植する

コードを移植したときにすべての機能が動作することを確認するには、コードを .NET Core に移植してテストすることをお勧めします。 テストするには、.NET Core 用にテストを構築して実行するテスト フレームワークを使用する必要があります。 現在のところ、次の 3 つの選択肢があります。

* [xUnit](https://xunit.github.io/)
   - [はじめに](http://xunit.github.io/docs/getting-started-dotnet-core.html)
   - [MSTest プロジェクトを xUnit に変換するツール](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
* [NUnit](http://www.nunit.org/)
  - [はじめに](https://github.com/nunit/docs/wiki/Installation)
  - [MSTest から NUnit への移行に関するブログ投稿](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
* [MSTest](https://msdn.microsoft.com/library/ms243147.aspx)

## <a name="recommended-approach-to-porting"></a>移植について推奨されるアプローチ

結局はコードを移植することです。 最終的に、実際のポート作業は .NET Framework コードの構築方法に大きく左右されます。 ここでは実際のコードベースで動作する可能性がある推奨アプローチを紹介します。

コードを移植するには、ライブラリの "ベース" から始めることをお勧めします。 ベースは、その他すべてが直接的または間接的に使用するデータ モデルまたは他の基本クラスおよびメソッドの場合があります。

1. 移植対象のライブラリのレイヤーをテストするテスト プロジェクトを移植します。
2. ライブラリの "ベース" を新しい .NET Core プロジェクトにコピーし、サポートする .NET Standard のバージョンを選択します。
3. 必要に応じてコードを変更し、コンパイルします。 多くの場合、NuGet パッケージの依存関係を `project.json` ファイルに追加する必要があります。
4. テストを実行し、必要な調整を行います。
5. 次のコード レイヤーを選択して移植し、手順 2 と 3 を繰り返します。

ライブラリのベースから系統的に移動し、必要に応じて各レイヤーをテストする場合、移植は体系的なプロセスになり、問題は 1 度に 1 レイヤーに分離されます。

