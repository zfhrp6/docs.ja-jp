---
title: ".NET Core コマンド ライン ツールの Preview 3 のアーキテクチャ"
description: "Preview 3 では、.NET Core のツールの階層化の方法全体が変わります。"
keywords: "CLI, 拡張, カスタム コマンド, .NET Core"
author: blackdwarf
manager: wpickett
ms.date: 11/12/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 233d365b582c274cd3a1f078846a6e854c7a6c95

---

<a name="high-level-overview-of-changes-in-cli-preview-3"></a>CLI Preview 3 の変更の概要
-----------------------------------------------

# <a name="overview"></a>概要
このドキュメントでは、`project.json` から MSBuild および `csproj` プロジェクト システムに移行する場合の概要を説明します。 ツールの新しい階層化の概要および、使用できる新しいツールとそれの全体の中での位置付けを示します。 この記事を読み終えると、MSBuild と `csproj` に移行した後の .NET Core ツールのすべてのツールをより理解できるようになります。 

> **注:** この記事では、Preview 3 の .NET Core のコマンド ライン ツールを使用する**必要はありません**。 使いなれたツールを使用し続けることができます。 この記事では、MSBuild に移行した場合、コマンド ライン ツールの階層全体およびアーキテクチャがどのように変わるかの全体像を示します。 

# <a name="moving-away-from-projectjson"></a>project.json から移行する
.NET Core の Preview 3 ツールの最大の違いは、プロジェクト システムが [project.json から csproj に移行](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)されることです。 このコマンド ライン ツールの Preview 3 バージョンは、project.json が完全にサポートされなくなる .NET Core コマンド ライン ツールの最初のリリースです。 これは、project.json を使用してアプリケーションやライブラリを構築、実行、発行できないことを意味します。 このバージョンのツールを使用するには、既存のプロジェクトを移行するか、新規に作成する必要があります。 

この移行の一環として、project.json プロジェクトの構築用に開発されたカスタム ビルド エンジンが、[MSBuild](https://github.com/Microsoft/msbuild) と呼ばれる、成熟した完全な機能を持つビルド エンジンに置き換えられました。 MSBuild は、プラットフォームの最初のリリース以来重要なテクノロジとなっているエンジンで、.NET コミュニティでは広く知られています。 MSBuild では .NET Core アプリケーションを構築するので、もちろん .NET Core に移植され、.NET Core を実行するすべてのプラットフォームで使用できるようになっています。 .NET Core の最大の保証の 1 つは、これがクロスプラット フォームの開発スタックであるということです。この動きによってこれは保証され続けるように努めました。

> **注:** MSBuild を初めて使用する方が、これについて深く学ぶには、最初に[既存ドキュメント](https://msdn.microsoft.com/en-us/library/dd637714.aspx)をお読みになってください。 

# <a name="the-tooling-layers"></a>ツールの階層
既存のプロジェクト システムとビルド エンジンが切り替わるにあたり、これらの変更によって .NET Core ツールのエコシステム全体の "レイヤー" には全体的な変更があるのかという疑問が当然生じると思います。 小さなものからコンポーネントまで、新しいものはありますか?

次の図で Preview 2 のレイヤーを簡単に再確認してみましょう。

![Preview 2 のツールの概要](media/p2-arch.png)

ツールのレイヤーはかなり単純です。 最下層には .NET Core のコマンド ライン ツールが基礎としてあります。 Visual Studio または VS コードなどのその他のすべての上位レベルのツールは、プロジェクトの構築、依存関係の復元に CLI に依存します。 これは、たとえば Visual Studio が復元操作を行う場合、CLI の `dotnet restore` コマンドが呼び出されることを意味します。 

新しいプロジェクト システムに移行すると、前の図は以下のように変わります。 

![Preview 3 のツールの概要](media/p3-arch.png)

主な違いは、CLI が基本的なレイヤーではなくなり、この役割が "共有 SDK コンポーネント" に置き換えられたことです。 この共有 SDK コンポーネントとは、一連のターゲットとそれに関連付けられている、コードのコンパイル、その発行、nuget パッケージの作成などを担当するタスクです。SDK 自体はオープン ソースであり、GitHub の [SDK リポジトリ](https://github.com/dotnet/sdk)から入手できます。 

> **注:** "ターゲット" とは、MSBuild が呼び出すことのできる名前付きの操作を意味する MSBuild の用語です。 これは、通常ターゲットが行うことを期待されているいくつかのロジックを実行する 1 つ以上のタスクと連結されています。 MSBuild では、`Copy` や `Execute` などの多数の既製ターゲットをサポートしています。また、ユーザーがマネージ コードを使用して、独自のタスクを記述し、それらのタスクをターゲットに実行させるよう定義することも可能です。 MSBuild のタスクの詳細については、「[MSDN](https://msdn.microsoft.com/en-us/library/ms171466.aspx)」を参照してください。 

すべてのツールセットは、CLI を含む、共有 SDK コンポーネントとそのターゲットを消費します。 たとえば、Visual Studio の次のバージョンでは .NET Core プロジェクトの依存関係の復元に `dotnet restore` コマンドを呼び出しません。直接 "Restore" ターゲットを使用します。 これらは MSBuild のターゲットであるため、これらの実行に未加工の MSBuild の [dotnet msbuild](dotnet-msbuild.md) コマンドを使用することも可能です。 

## <a name="preview-3-cli-commands"></a>Preview 3 の CLI コマンド
共有 SDK コンポーネントとは、大多数の既存の CLI コマンドが MSBuild のタスクやターゲットとして再実装されたものです。 これは CLI コマンドやツールセットの使用にどのような意味があるのでしょうか? 

使用の観点からは、CLI の使用方法には変わりはありません。 CLI にはまだ Preview 2 リリースにある主要なコマンドがあります。

* `new`
* `restore`
* `run` 
* `build`
* `publish`
* `test`
* `pack` 

これらのコマンドは、現在も (新しいプロジェクトの作成、構築、発行、作成などの) 目的の動作をします。 オプションの多くは変更されず残っています。変更の詳細については、コマンドのヘルプ画面を (`dotent <command> --help` コマンドを使用して) 確認するか、このサイトの Preview 3 ドキュメントを参照してください。 

実行の観点から見た場合、CLI コマンドはそのパラメーターを取り、必要なプロパティを設定して目的のターゲットを実行する「未加工」の MSBuild への呼び出しを作成します。 次の図でこれを分かりやすく説明します。 

    `dotnet publish -o pub -c Release`. 
    
このコマンドは、"Release" 構成を使用してアプリケーションを `pub` フォルダーに発行します。 このコマンドは、内部では次の MSBuild の呼び出しに変換されます。 

    `dotnet msbuild /t:Publish /p:OutputPath=pub /p:Configuration`

`new` と `run` のコマンドは、MSBuild のターゲットとして実装されておらず、このルールの主な例外です。 

# <a name="conclusion"></a>まとめ 
このドキュメントでは、Preview 3 で導入される CLI ツールのアーキテクチャと機能全体に対する変更の概要を示しました。 共有 SDK コンポーネントの概念を導入するとともに、Preview 3 での CLI コマンドのしくみを技術的な観点から説明しました。 




<!--HONumber=Nov16_HO3-->


