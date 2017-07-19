---
title: ".NET Core とオープン ソース | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: 8
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 24ae3c7e78d43960cf8c4127a164caa7edb69254
ms.openlocfilehash: c6e7a2658cffa5692ffe515f6d07918f550d72c6
ms.contentlocale: ja-jp
ms.lasthandoff: 05/25/2017

---
<a id="net-core-and-open-source" class="xliff"></a>
# .NET Core とオープン ソース
このトピックでは、.NET Core の概要のほか、詳細情報の入手方法を説明します。 .NET Core に関するトピックの完全な一覧については、[「.NET Core のガイド」](../../core/index.md) を参照してください。
  
<a name="BKMK_WhatisNETCore"></a>   
<a id="what-is-net-core" class="xliff"></a>
## .NET Core とは何ですか?  
 .NET Core は、モジュール形式のクロスプラットフォームかつオープン ソースを実装した汎用の .NET プラットフォームです。 .NET Framework と同じ API の多くが含まれるほか (ただし、.NET Core の方が数が少ない) 、ランタイム、フレームワーク、コンパイラ、およびさまざまなオペレーティング システムやチップ ターゲットをサポートするツールのコンポーネントが含まれます。 .NET Core の実装は、主に ASP.NET Core のワークロードによるものですが、新しいランタイムの必要性とユーザーの要望にも後押しされました。 この実装は、デバイス、クラウド、および埋め込み/IoT のシナリオで使用できます。  
  
 .NET Core を使用する場合、[.NET Core のホームページ](https://www.microsoft.com/net/core)を参照してください。  
  
 .NET Core の主な特徴を次に示します。  
  
-   **クロス プラットフォーム:** .NET Core には、ターゲットとするプラットフォームに関係なく、必要とするアプリケーション機能を実装したり、そのコードを再使用したりするための主な機能が備わっています。 現在、Windows、Linux と macOS の 3 つの主要オペレーティング システム (OS) をサポートしています。 サポートされている複数の OS で、修正せずに動作するアプリやライブラリを作成することができます。 サポートされるオペレーティング システムの一覧については、[「.NET Core Roadmap」](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core ロードマップ) を参照してください。
  
-   **オープン ソース:** .NET Core は [.NET Foundation ](http://www.dotnetfoundation.org/)が管理している多くのプロジェクトの 1 つで、[GitHub](https://github.com/) で入手することができます。  .NET Core をオープン ソース プロジェクトとして使用すると、開発プロセスの透明性が高まるほか、コミュニティが活発化して交流が促進されます。  
  
-   **柔軟な展開:** アプリを展開する主な方法には、フレームワークに依存する展開と自己完結型の展開の 2 つがあります。 フレームワークに依存して展開する場合、アプリとサード パーティの依存関係のみがインストールされ、アプリを使用できるようにするには、.NET Core のシステム全体のバージョンが必要です。  自己完結型で展開する場合、アプリの作成に使用される .NET Core バージョンが、アプリやサード パーティの依存関係と共に展開され、他のバージョンと並行して実行することができます。    詳しくは、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」をご覧ください。

-   **モジュール形式:** .NET Core は、小規模のアセンブリ パッケージで NuGet を介してリリースされるためモジュール形式となっています。 .NET Core はコア機能のほとんどが含まれる 1 つの大きなアセンブリではなく、中心的な機能が含まれる比較的小さなパッケージとして提供されています。 これによって開発モデルがよりアジャイル化されるため、必要な NuGet パッケージだけが含まれるようにアプリを最適化することができます。 小さいアプリ領域の利点には、セキュリティの強化、サービスの削減、パフォーマンスの向上、従量課金モデルによるコスト削減などがあります。  
  
<a id="the-net-core-platform" class="xliff"></a>
## .NET Core プラットフォーム  
 .NET Core プラットフォームは複数コンポーネントで構成され、マネージ コンパイラ、ランタイム、基本クラス ライブラリ、および ASP.NET Core などの多数のアプリケーション モデルが含まれます。 さまざまなコンポーネントの詳細や、実際の操作については、以下の [GitHub](https://github.com/) リポジトリを参照してください。  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX - .NET Core foundational libraries (CoreFX - .NET Core の基本的なライブラリ)](https://github.com/dotnet/corefx)  
  
-   [CoreCLR - .NET Core runtime (CoreCLR - .NET Core ランタイム)](https://github.com/dotnet/coreclr)  
  
-   [CLI - .NET Core command-line tools (CLI - .NET Core のコマンド ライン ツール)](https://github.com/dotnet/cli)  
  
-   [Roslyn - .NET Compiler Platform (.NET コンパイラ プラットフォーム)](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
<a id="see-also" class="xliff"></a>
## 関連項目  
 [.NET Core のホーム ページ](https://www.microsoft.com/net/core)   
 [.NET Core ドキュメント サイト](../core/index.md)   
 [ASP.NET Core ドキュメント](/aspnet/core/)
