---
title: "ターゲット フレームワーク | Microsoft Docs"
description: ".NET Core アプリケーションおよびライブラリのターゲット フレームワークに関連する情報。"
keywords: ".NET, .NET Core, フレームワーク, TFM"
author: richlander
ms.author: mairaw
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45835eb80642253f80ea630ae9db1ac766b72b9c
ms.openlocfilehash: 11c1f11e4f8354b7573d03e680cf4a8a16fa26d9
ms.contentlocale: ja-jp
ms.lasthandoff: 05/11/2017

---

# <a name="target-frameworks"></a>ターゲット フレームワーク

*フレームワーク*は、アプリとライブラリの作成に使用するオブジェクト、メソッド、ツールを定義します。 .NET Framework は、主に Windows オペレーティング システムを実行しているシステム上で実行されるアプリとライブラリの作成に使用されます。 .NET Core には、さまざまなオペレーティング システムで実行されるアプリとライブラリを構築できるフレームワークが含まれています。

*フレームワーク*と*プラットフォーム*という用語は、文章の中での使用方法によっては混乱することがあります。 さらに悪いことに、文脈によっては*プラットフォーム*という用語が別の意味になることもあります。 たとえば、".NET Core" という言葉は、アプリとライブラリを構築する文脈では ".NET Core フレームワーク" の意味で、アプリとライブラリ コードを実行する文脈では ".NET Core プラットフォーム" の意味で出現します。 *コンピューティング プラットフォーム*では、アプリケーションが*どこで、どのように*実行されるかについて説明します。 .NET Core は、[.NET Core 共通言語ランタイム (CoreCLR)](https://github.com/dotnet/coreclr) を使用してコードが実行されるので、これもプラットフォームです。 .NET Framework のフレームワーク オブジェクト、メソッド、およびツールを使用して開発されたアプリとライブラリ コードを実行するために[共通言語ランタイム (CLR)](clr.md) を使用している .NET Framework の場合も同様です。 "クロスプラットフォーム" という用語はドキュメントでよく見られますが、この用語を見かけたら、"クロスプラットフォーム システムとクロスアーカイブ (x86、x64、arm)" が通常、執筆者が伝えたいと思う意味なので、これを意味していると考えるのではないでしょうか。

フレームワークのオブジェクトとメソッドは、アプリケーション プログラミング インターフェイス (API) と呼ばれます。 フレームワークの API は、[Visual Studio](https://www.visualstudio.com/)、[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)、[Visual Studio Code](https://code.visualstudio.com/)、およびその他の統合開発環境 (IDE) とエディターで使用され、開発用の適切なオブジェクトとメソッドのセットを提供しています。 また、フレームワークは、アプリまたはライブラリで対象としているフレームワークに適したパッケージを確実に作成して使用するため、NuGet パッケージの運用と使用の両方で [NuGet](https://www.nuget.org/) でも使用されます。

*1 つのフレームワークを対象にする*か、複数のフレームワークを対象にすると、使用する API のセットと API のバージョンが決まります。 フレームワークを参照するには、製品名ごと、長い形式または短い形式のフレームワーク名ごと、またはファミリごとという複数の方法があります。

## <a name="referring-to-frameworks"></a>フレームワークを参照する

フレームワークを参照する方法は複数あります。そのほとんどについてこの .NET Core ドキュメントで使用します。 たとえば .NET Framework 4.6.2 を使用する場合は、次の形式が使用されます。

**成果物を参照する**

.NET プラットフォームまたはランタイムを参照することができます。 両方とも有効です。

* .NET Framework 4.6.2
* .NET 4.6.2

**フレームワークを参照する**

長い形式または短い形式の TFM を使用して、フレームワークまたはフレームワークの対象を参照することができます。 両方とも有効です。

* `.NETFramework,Version=4.6.2`
* `net462`

**フレームワークのファミリを参照する**

長い形式または短い形式のフレームワーク ID を使用して、フレームワークのファミリを参照することができます。 両方とも有効です。

* `.NETFramework`
* `net`

## <a name="latest-framework-versions"></a>最新のフレームワークバージョン

次の表では、使用できるフレームワークのセットと、これらが参照される方法、およびこれらが実装する [.NET Standard Library](library.md) のバージョンを定義します。 これらのフレームワークのバージョンは、最新の安定したバージョンです。 プレリリース バージョンは記載されていません。

| フレームワーク             | [最新バージョン] | ターゲット フレームワーク モニカー (TFM) | コンパクトなターゲット フレームワーク モニカー (TFM) | .NET Standard バージョン | メタパッケージ |
| :-------------------: | :------------: | :----------------------------: | :------------------------------------: | :-------------------: | :---------: |
| .NET Standard         | 1.6.1          | .NETStandard,Version=1.6       | netstandard1.6                         | N/A                   | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) |
| .NET Core アプリケーション | 1.1.1          | .NETCoreApp,Version=1.1        | netcoreapp1.1                          | 1.6                   | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) |
| .NET Framework        | 4.6.2          | .NETFramework,Version=4.6.2    | net462                                 | 1.5                   | N/A |

## <a name="supported-frameworks"></a>サポートされるフレームワーク

通常、フレームワークは、短いターゲット フレームワーク モニカー (*TFM*) で参照されます。 .NET Standard の場合、1 つの参照で複数のフレームワークを参照できるように、*TxM* に汎用化されています。 NuGet クライアントは次のフレームワークをサポートしています。 同等のものがかっこ (`[]`) 内に示されます。

| 名前                       | 省略形 | TFM/TxM                                    |
| -------------------------- | ------------ | -------------------------------------------- |
| .NET Standard              | netstandard  | netstandard1.0                               |
|                            |              | netstandard1.1                               |
|                            |              | netstandard1.2                               |
|                            |              | netstandard1.3                               |
|                            |              | netstandard1.4                               |
|                            |              | netstandard1.5                               |
|                            |              | netstandard1.6                               |
| .NET Core                  | netcoreapp   | netcoreapp1.0                                |
|                            |              | netcoreapp1.1                                |
| .NET Framework             | net          | net11                                        |
|                            |              | net20                                        |
|                            |              | net35                                        |
|                            |              | net40                                        |
|                            |              | net403                                       |
|                            |              | net45                                        |
|                            |              | net451                                       |
|                            |              | net452                                       |
|                            |              | net46                                        |
|                            |              | net461                                       |
|                            |              | net462                                       |
| Windows ストア              | netcore      | netcore [netcore45]                          |
|                            |              | netcore45 [win、win8]                        |
|                            |              | netcore451 [win81]                           |
| .NET Micro Framework       | netmf        | netmf                                        |
| Silverlight                | sl           | sl4                                          |
|                            |              | sl5                                          |
| Windows Phone              | wp           | wp [wp7]                                     |
|                            |              | wp7                                          |
|                            |              | wp75                                         |
|                            |              | wp8                                          |
|                            |              | wp81                                         |
|                            |              | wpa81                                        |
| ユニバーサル Windows プラットフォーム | uap          | uap [uap10.0]                                |
|                            |              | uap10.0 [win10] [netcore50]                  |

## <a name="deprecated-frameworks"></a>使用されていないフレームワーク

次のフレームワークは使用されていません。 これらのフレームワークを対象とするパッケージは、指定されている代替のフレームワークに移行するようにしてください。

| 使用されていないフレームワーク | Replacement |
| -------------------- | ----------- |
| aspnet50             | netcoreapp  |
| aspnetcore50         |             |
| dnxcore50            |             |
| dnx                  |             |
| dnx45                |             |
| dnx451               |             |
| dnx452               |             |
| dotnet               | netstandard |
| dotnet50             |             |
| dotnet51             |             |
| dotnet52             |             |
| dotnet53             |             |
| dotnet54             |             |
| dotnet55             |             |
| dotnet56             |             |
| netcore50            | uap10.0     |
| win                  | netcore45   |
| win8                 | netcore45   |
| win81                | netcore451  |
| win10                | uap10.0     |
| winrt                | netcore45   |

## <a name="precedence"></a>優先順位

フレームワークの番号は相互の関連性や互換性を示していますが、必ずしも同一ではありません。

| フレームワーク                        | 使用可能   |
| -------------------------------- | --------- |
| uap (ユニバーサル Windows プラットフォーム) | win81     |
|                                  | wpa81     |
|                                  | netcore50 |
| win (Windows ストア)              | winrt     |
|                                  | winrt45   |

## <a name="net-standard"></a>.NET Standard

[.NET Standard](https://github.com/dotnet/standard) は、バイナリ互換フレームワーク間の参照を簡易化し、1 つのターゲット フレームワークで複数のフレームワークの組み合わせを参照できます。 詳細については、「[.NET Standard Library](library.md)」を参照してください。

[NuGet Tools の Get Nearest Framework Tool](http://nugettoolsdev.azurewebsites.net/) では、プロジェクトのフレームワークに基づいて、パッケージ内で使用できる複数のフレームワーク アセットから、1 つのフレームワークを選択するために使用する NuGet ロジックをシミュレートしています。 このツールを使用するには、1 つのプロジェクト フレームワークと 1 つ以上のパッケージ フレームワークを入力します。 **[送信]** ボタンを選択します。 列挙したパッケージのフレームワークが、指定したプロジェクトのフレームワークと互換性があるかどうかが表示されます。

## <a name="portable-class-libraries"></a>ポータブル クラス ライブラリ

ポータブル クラス ライブラリの詳細については、NuGet ドキュメントの「*Target Framework*」(ターゲット フレームワーク) の「[Portable Class Libraries](https://docs.microsoft.com/nuget/schema/target-frameworks#portable-class-libraries)」(ポータブル クラス ライブラリ) セクションを参照してください。 Stephen Cleary がサポートされる PCL を列挙するツールを作成しています。 詳細については、「[Framework Profiles in .NET](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)」(.NET のフレームワーク プロファイル) を参照してください。

