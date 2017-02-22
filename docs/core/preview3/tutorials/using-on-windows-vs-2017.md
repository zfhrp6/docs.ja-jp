---
title: "Visual Studio 2017 を使用した Windows での .NET Core の概要 | Microsoft Docs"
description: "Visual Studio 2017 を使用した Windows での .NET Core の概要"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 01/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 613c65d0-f773-41b8-ba0e-83f6a82a0b30
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: cc2c2853bc31e161d1fe0de4edc71d15281c6d24

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2017-net-core-tools-rc4"></a>Visual Studio 2017 を使用した Windows での .NET Core の概要 (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 Visual Studio 2015 - .NET Core Tools Preview 2 バージョンについては、「[Visual Studio 2015 を使用した Windows での .NET Core の概要](../../tutorials/using-on-windows.md)」トピックを参照してください。

Visual Studio 2017 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。 このドキュメントでは、Visual Studio と .NET Core を使用して、とても単純なコンソール アプリケーションをビルドするために必要な手順について説明します。

## <a name="prerequisites"></a>前提条件

[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。

## <a name="getting-started"></a>作業の開始

次の手順では、.NET Core コンソール アプリケーションの開発用に Visual Studio 2017 を設定します。

1. Visual Studio を開き、**[ファイル]** メニューで **[新規作成]**、**[プロジェクト]** の順に選択します。

2. **[新しいプロジェクト]** ダイアログの **[テンプレート]** の一覧で、**[Visual C#]** ノードを展開し、**[.NET Core]** を選択します。 **コンソール アプリケーション (.NET Core)** 用、**クラス ライブラリ (.NET Standard)** 用、**xUnit テスト プロジェクト (.NET Core)** 用、**クラス ライブラリ (.NET Core)** 用、**ASP.NET Core Web アプリケーション (.NET Core)** 用の&5; つのプロジェクト テンプレートが表示されます。 **[コンソール アプリケーション (.NET Core)]** を選択し、プロジェクトの名前を入力して場所を選択してから [OK] をクリックします。

  ![新しいプロジェクト: コンソール アプリケーション](media/new-project-console-app.png)

3. 結果のプロジェクトには、コンソールに "Hello World" と出力する単一の C# ファイルがあります。

  ![コンソール アプリケーション プロジェクト](media/console-app-solution.png)

このアプリケーションは、F5 キーを使用する場合はデバッグ モードで、Ctrl + F5 キーを使用する場合はリリース モードで実行できます。 また、ブレークポイントを設定し、実行を中断して変数を調べたり、必要なコードをさらに書き込んだりすることもできます。

コーディングを楽しんでください。

## <a name="next-steps"></a>次の手順

この概要をお読みになっただけでは、再利用可能なライブラリとテストを含む、より高度なソリューションをビルドする方法が想像できないこともあるでしょう。 「[Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築](using-on-windows-vs-2017-full-solution.md)」トピックで、その方法について説明します。



<!--HONumber=Feb17_HO2-->


