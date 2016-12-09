---
title: "Visual Studio 2017 を使用した Windows での .NET Core の概要"
description: "Visual Studio 2017 を使用した Windows での .NET Core の概要"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 71eab6216e116b99927dfeaa8ce3cf70bcc08a5e
ms.openlocfilehash: 4437f44523bcc4e8517de5b6be42a63439f817d7

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2017"></a>Visual Studio 2017 を使用した Windows での .NET Core の概要

著者: [Bertrand Le Roy](https://github.com/bleroy)、[Phillip Carter](https://github.com/cartermp)

Visual Studio 2017 は、.NET Core アプリケーション開発用の機能をすべて備えた開発環境を提供します。 このドキュメントでは、Visual Studio と .NET Core を使用して、とても単純なコンソール アプリケーションをビルドするために必要な手順について説明します。

## <a name="prerequisites"></a>前提条件

[前提条件のページ](../windows-prerequisites.md)の指示に従って、環境を更新します。

## <a name="getting-started"></a>作業の開始

次の手順では、.NET Core コンソール アプリケーションの開発用に Visual Studio 2017 を設定します。

1. Visual Studio を開き、**[ファイル]** メニューで **[新規作成]**、**[プロジェクト]** の順に選択します。

2. **[新しいプロジェクト]** ダイアログの **[テンプレート]** の一覧で、**[Visual C#]** ノードを展開し、**[.NET Core]** を選択します。 **コンソール アプリケーション (.NET Core)** 用、**単体テスト プロジェクト (.NET Core)** 用、**クラス ライブラリ (.NET Core)** 用、**ASP.NET Core Web アプリケーション (.NET Core)** 用の 4 つのプロジェクト テンプレートが表示されます。 **[コンソール アプリケーション (.NET Core)]** を選択し、プロジェクトの名前を入力して場所を選択してから [OK] をクリックします。

  ![新しいプロジェクト: コンソール アプリケーション](media/new-project-console-app.png)

3. 結果のプロジェクトには、コンソールに "Hello World" と出力する単一の C# ファイルがあります。

  ![コンソール アプリケーション プロジェクト](media/console-app-solution.png)

このアプリケーションは、F5 キーを使用する場合はデバッグ モードで、Ctrl + F5 キーを使用する場合はリリース モードで実行できます。 また、ブレークポイントを設定し、実行を中断して変数を調べたり、必要なコードをさらに書き込んだりすることもできます。

コーディングを楽しんでください。

## <a name="what-to-do-next"></a>次の作業

この概要をお読みになっただけでは、再利用可能なライブラリとテストを含む、より高度なソリューションをビルドする方法が想像できないこともあるでしょう。 「[Visual Studio 2017 を使用した Windows での完全な .NET Core ソリューションの構築](using-on-windows-vs-2017-full-solution.md)」トピックで、その方法について説明します。



<!--HONumber=Nov16_HO3-->


