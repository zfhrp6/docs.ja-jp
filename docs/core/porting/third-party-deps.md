---
title: .NET Core への移植 - サードパーティの依存関係を分析する
description: .NET Framework から .NET Core にプロジェクトを移植するために、サードパーティの依存関係を分析する方法を説明します。
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: be8d5a60977c7863136a1661a60e3bf23c0eb93e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-your-third-party-dependencies"></a>サードパーティの依存関係を分析する

.NET Core または .NET Standard にコードを移植する場合、移植プロセスの最初のステップとして、サードパーティの依存関係を理解します。 サードパーティの依存関係は、プロジェクトで参照する [NuGet パッケージ](#analyze-referenced-nuget-packages-on-your-project)または [DLL](#analyze-dependencies-that-arent-nuget-packages) です。 それぞれの依存関係を評価し、.NET Core と互換性のない依存関係に対して代替計画を作成します。 この記事では、依存関係が .NET Core と互換性があるかどうかを判別する方法を示します。

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>プロジェクトで参照される NuGet パッケージを分析する

プロジェクトで NuGet パッケージを参照する場合は、.NET Core と互換性があるかどうかを確認する必要があります。
これを行う場合、次の 2 つの方法があります。

* [NuGet パッケージ エクスプローラー アプリの使用](#analyze-nuget-packages-using-nuget-package-explorer) (最も信頼性の高い方法)。
* [nuget.org サイトの使用](#analyze-nuget-packages-using-nugetorg)。

パッケージの分析後、NET Core と互換性がなく、.NET Framework のみをターゲットとする場合は、[.NET Framework 互換モード](#net-framework-compatibility-mode)が移植プロセスに役立つかどうかを確認できます。

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet パッケージ エクスプローラーを使用して NuGet パッケージを分析する

NuGet パッケージ自体はフォルダーのセットであり、プラットフォーム固有のアセンブリが含まれます。 したがって、パッケージ内に互換性のあるアセンブリを含むフォルダーがあるかどうかを確認する必要があります。

NuGet パッケージ フォルダーを調べる最も簡単な方法は、[NuGet パッケージ エクスプローラー](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用することです。 これをインストールした後、次の手順を使用してフォルダー名を確認します。

1. NuGet パッケージ エクスプローラーを開きます。
2. **[Open package from online feed]\(オンライン フィードからパッケージを開く\)** をクリックします。
3. パッケージの名前を検索します。
4. 検索結果からパッケージ名を選択し、**[開く]** をクリックします。
5. 右側にある *lib* フォルダーを展開し、フォルダー名を確認します。

次のいずれかの名前のフォルダーを探します。

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

これらの値は[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) であり、[.NET Standard](../../standard/net-standard.md)、.NET Core、および .NET Core と互換性がある従来のポータブル クラス ライブラリ (PCL) プロファイルのバージョンにマップされます。

> [!IMPORTANT]
> パッケージでサポートされる TFM を見ると、`netcoreapp*` に互換性はあるものの、.NET Core プロジェクトのみを対象としており、.NET Standard プロジェクトを対象としていないことがわかります。
> 他の .NET Core アプリで使用できるのは、`netstandard*` ではなく、`netcoreapp*` のみをターゲットとするライブラリだけです。

また、プレリリース版の .NET Core で使用されるレガシ TFM にも、互換性のあるものがあります。

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

これらの TFM がコードで動作する可能性はありますが、互換性は保証されていません。 このような TFM を含むパッケージは、プレリリース版の .NET Core パッケージで構築されています。 これらの TFM を使用するパッケージが .NET Standard ベースに更新されるか、また、更新される場合はいつ行われるかを確認してください。

> [!NOTE]
> 従来の PCL またはプレリリースの .NET Core ターゲットを対象とするパッケージを使用するには、プロジェクト ファイルで `PackageTargetFallback` MSBuild 要素を使用する必要があります。
> MSBuild 要素の詳細については、「[`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback)」を参照してください。

### <a name="analyze-nuget-packages-using-nugetorg"></a>nuget.org を使用して NuGet パッケージを分析する

[nuget.org](https://www.nuget.org/) のパッケージ ページの **[Dependencies]\(依存関係\)** セクションで、各パッケージでサポートされる TFM を確認することもできます。

サイトを使用するのが互換性を確認するより簡単な方法ですが、**依存関係**情報はすべてのパッケージのサイトで利用できるわけではありません。

### <a name="net-framework-compatibility-mode"></a>.NET Framework 互換モード

NuGet パッケージの分析後、ほとんどの NuGet パッケージと同様に、.NET Framework のみがターゲットであることがわかる場合があります。

.NET Standard 2.0 以降、.NET Framework 互換モードが導入されました。 この互換モードにより、.NET Standard および .NET Core プロジェクトは .NET Framework ライブラリを参照できます。 .NET Framework ライブラリの参照はすべてのプロジェクトで機能するわけではありません (例えばライブラリで Windows Presentation Foundation (WPF) API を使用していても、多くの移植シナリオがブロック解除される場合など)。

[Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections) など、プロジェクトで .NET Framework をターゲットとする NuGet パッケージを参照すると、次の例のようなパッケージ フォールバック警告 ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) が表示されます。

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

この警告は、パッケージを追加したとき、およびプロジェクトでそのパッケージを確実にテストするためにビルドするたびに表示されます。 プロジェクトが予期したとおりに動作している場合は、Visual Studio でパッケージ プロパティを編集するか、任意のコード エディターでプロジェクト ファイルを手動で編集して、この警告を非表示にすることができます。

プロジェクト ファイルを編集して警告を非表示にするには、警告を非表示にするパッケージの `PackageReference` エントリを見つけて、`NoWarn` 属性を追加します。 `NoWarn` 属性では、すべての警告 ID のコンマ区切りリストを受け入れます。 次の例は、プロジェクト ファイルを手動で編集して、`Huitian.PowerCollections` パッケージの `NU1701` 警告を非表示にする方法を示しています。

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio でコンパイラ警告を非表示にする方法の詳細については、「[NuGet パッケージの警告を非表示にする](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages)」を参照してください。

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet パッケージの依存関係が .NET Core で動作しない場合の対処方法

依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。

1. プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。
2. [nuget.org](https://www.nuget.org/) で直接作成者に連絡することができます。パッケージを検索し、パッケージのページの左側にある **[Contact Owners]\(所有者に問い合わせる\)** をクリックします。
3. 使用していたパッケージと同じタスクを実行する、.NET Core で実行される別のパッケージを検索することができます。
4. パッケージが行っていたコードを自分で記述できます。
5. 少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。

オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、ボランティアであることを忘れないでください。 彼らは、その分野に関心があるために無償で作業を行っており、多くの場合、日中に別の仕事を抱えています。 したがって、.NET Core のサポートを求めるために連絡する際には、この点を考慮してください。

上記のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。

.NET チームは .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。 使用したいライブラリについて、dotnet@microsoft.com にメールを送ることができます。

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet パッケージではない依存関係を分析する

ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。 その依存関係の移植性を調べる唯一の方法が、[.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) ツールを実行することです。 このツールでは、.NET Framework をターゲットとするアセンブリを分析し、.NET Core などの他の .NET プラットフォームに移植できない API を特定できます。 このツールはコンソール アプリケーションまたは [Visual Studio 拡張機能](../../standard/analyzers/portability-analyzer.md)として実行できます。

## <a name="next-steps"></a>次の手順

ライブラリを移植している場合は、「[Porting your Libraries](libraries.md)」(ライブラリへの移植) を参照してください。
