---
title: Roslyn ベースのアナライザー - .NET
description: 問題を検出し、各問題について修正を提案する Roslyn ベースのアナライザーについて説明します。
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a>Roslyn ベースのアナライザー

Roslyn ベースのアナライザーでは、.NET Compiler SDK (Roslyn の API) を使用して、プロジェクトのソース コードを分析し、問題の検出と修正の提案を行います。 検出する問題のクラスは、バグを起こしやすい慣習から API の互換性に関するセキュリティの問題まで、アナライザーによってさまざまです。

Roslyn ベースのアナライザーは対話型であり、ビルド中にも動作します。 Visual Studio またはコマンド ラインからビルドする際に、アナライザーはさまざまなガイダンスを提供します。

Visual Studio でコードを編集する場合、コードを変更するとアナライザーが実行され、問題を含むコードの作成後すぐに考えられる問題がキャッチされます。 すべての問題は波線で強調表示されます。 Visual Studio に表示される電球をクリックすると、その問題に対して考えられる修正方法がアナライザーによって提案されます。 Visual Studio またはコマンド ラインでプロジェクトをビルドすると、すべてのソース コードが分析され、潜在的な問題の全リストがアナライザーによって示されます。 次の図に例を示します。

![フレームワーク アナライザーによって報告される問題](./media/framework-analyzers-2.png)

Roslyn ベースのアナライザーでは、エラー、警告、または問題の重大度に基づく情報として、潜在的な問題が報告されます。

Roslyn ベースのアナライザーは、プロジェクト内に NuGet パッケージとしてインストールします。 構成されたアナライザーと各アナライザーに対するすべての設定は復元され、そのプロジェクト用の任意の開発者のマシンで実行されます。

> [!NOTE]
> Roslyn ベースのアナライザーのユーザー エクスペリエンスは、FxCop の旧バージョンのようなコード分析ライブラリや、セキュリティ分析ツールとは異なるものです。  明示的に Roslyn ベースのアナライザーを実行する必要はありません。 Visual Studio の [分析] メニューで [コード分析の実行] メニュー項目を使用する必要はありません。 Roslyn ベースのアナライザーは、ユーザーの作業と同期して実行されます。 

## <a name="more-information-on-specific-analyzers"></a>特定のアナライザーについての詳細

このセクションでは、次のアナライザーについて説明します。

[API アナライザー](api-analyzer.md): このアナライザーでは、コードの互換性の潜在的リスクや、非推奨の API の使用が調べられます。    
[フレームワーク アナライザー](framework-analyzer.md): このアナライザーでは、コードが .NET Framework アプリケーションのガイドラインに従っているかどうかが調べられます。 これらの規則には、セキュリティに基づく推奨事項がいくつか含まれます。
