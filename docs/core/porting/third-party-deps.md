---
title: ".NET Core への移植 - サードパーティの依存関係の分析"
description: ".NET Core への移植 - サードパーティの依存関係の分析"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 5b7bbc0718817365df63db4d8ca7e4cf8871abae
ms.lasthandoff: 03/02/2017

---

# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>.NET Core への移植 - サードパーティの依存関係の分析

移植プロセスの最初の手順は、サード パーティの依存関係を理解することです。  .NET Core でまだ実行されていないもの (がある場合) はどれかを確認し、それらに対して代替計画を作成する必要があります。

## <a name="prerequisites"></a>必須コンポーネント

この記事は、Windows および Visual Studio を使用しており、最新の .NET Framework で実行されるコードがあることを前提にしています。

## <a name="analyzing-nuget-packages"></a>NuGet パッケージの分析

NuGet パッケージの移植性の分析は非常に簡単です。  NuGet パッケージはそれ自体がプラットフォーム固有のアセンブリを含むフォルダーのセットであるため、.NET Core のアセンブリが含まれるフォルダーがあるかどうかを確認するだけです。

[NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用すると、最も簡単に NuGet パッケージ フォルダーを調べることができます。  これを行う方法を次に示します。

1. NuGet Package Explorer をダウンロードして開きます。
2. 「Open package from online feed」 (オンライン フィードからパッケージを開く) をクリックします。
3. パッケージの名前を検索します。
4. 右側にある "lib" フォルダーを展開し、フォルダー名を確認します。

そのパッケージのページの **[Dependencies]** (依存関係) セクションで、[nuget.org](https://www.nuget.org/) でサポートされているパッケージを確認することもできます。

どちらの場合でも、次のいずれかの名前のフォルダーまたはエントリを [nuget.org](https://www.nuget.org/) で探す必要があります。

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

これらは [.NET 標準ライブラリ](../../standard/library.md)のバージョンにマップされる Target Framework Moniker (TFM) および .NET Core と互換性がある従来のポータブル クラス ライブラリ (PCL) プロファイルです。  `netcoreapp1.0` には互換性はありますが、アプリケーションを対象としており、ライブラリは対象としていません。  `netcoreapp1.0` をベースとするライブラリを使用する場合は問題ありませんが、そのライブラリが他の `netcoreapp1.0` アプリケーションで使用される*以外*のことを想定していない場合があります。

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

**これらは、あなたのコードで動作する可能性が高いですが、互換性は保証されていません**。  このような TFM を含むパッケージは、プレリリース版の .NET Core パッケージで構築されています。  このようなパッケージが `netstandard` ベースに更新されるか、また、更新される場合はいつ行われるかを確認してください。

> [!NOTE]
> 従来の PCL またはプレリリースの .NET Core ターゲットを対象とするパッケージを使用するには、`project.json` ファイルで `imports` ディレクティブを使用する必要があります。

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet パッケージの依存関係が .NET Core で動作しない場合の対処方法

依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。

1. プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。
2. パッケージを検索してパッケージのページの左側にある 「Contact Owners」 (オーナーに連絡する) をクリックすることで、[nuget.org](https://www.nuget.org/) の作成者に直接連絡することができます。
3. .NET Core で実行され、使っていたパッケージと同じタスクを実行する別のパッケージを探すことができます。
4. パッケージが行っていたコードを自分で記述できます。
5. 少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。

オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、その分野に関心があるために無償で作業を行っているボランティアであり、日中に別の仕事を抱えていることを忘れないでください。 連絡を取る場合は、.NET Core サポートについて質問する前に、ライブラリについて肯定的なコメントを述べるとよいでしょう。

上記のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。

.NET チームは次の .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。 使用したいライブラリについて、dotnet@microsoft.comにメールを送ることもできます。

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>NuGet パッケージではない依存関係の分析

ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。  その依存関係の移植性を調べる唯一の方法が、[ApiPort ツール](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)を実行することです。

## <a name="next-steps"></a>次の手順

ライブラリを移植している場合は、「[Porting your Libraries](libraries.md)」(ライブラリへの移植) を参照してください。

