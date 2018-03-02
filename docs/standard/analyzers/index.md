---
title: "Roslyn ベースのアナライザー - .NET"
description: "問題を検出し、各問題について修正を提案する Roslyn ベースのアナライザーについて説明します。"
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
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="6c7f2-104">Roslyn ベースのアナライザー</span><span class="sxs-lookup"><span data-stu-id="6c7f2-104">The Roslyn based Analyzers</span></span>

<span data-ttu-id="6c7f2-105">Roslyn ベースのアナライザーでは、.NET Compiler SDK (Roslyn の API) を使用して、プロジェクトのソース コードを分析し、問題の検出と修正の提案を行います。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-105">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="6c7f2-106">検出する問題のクラスは、バグを起こしやすい慣習から API の互換性に関するセキュリティの問題まで、アナライザーによってさまざまです。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-106">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="6c7f2-107">Roslyn ベースのアナライザーは対話型であり、ビルド中にも動作します。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-107">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="6c7f2-108">Visual Studio またはコマンド ラインからビルドする際に、アナライザーはさまざまなガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-108">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="6c7f2-109">Visual Studio でコードを編集する場合、コードを変更するとアナライザーが実行され、問題を含むコードの作成後すぐに考えられる問題がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-109">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="6c7f2-110">すべての問題は波線で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-110">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="6c7f2-111">Visual Studio に表示される電球をクリックすると、その問題に対して考えられる修正方法がアナライザーによって提案されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-111">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="6c7f2-112">Visual Studio またはコマンド ラインでプロジェクトをビルドすると、すべてのソース コードが分析され、潜在的な問題の全リストがアナライザーによって示されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-112">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="6c7f2-113">次の図に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-113">The following figure shows one example.</span></span>

![フレームワーク アナライザーによって報告される問題](./media/framework-analyzers-2.png)

<span data-ttu-id="6c7f2-115">Roslyn ベースのアナライザーでは、エラー、警告、または問題の重大度に基づく情報として、潜在的な問題が報告されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-115">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="6c7f2-116">Roslyn ベースのアナライザーは、プロジェクト内に NuGet パッケージとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-116">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="6c7f2-117">構成されたアナライザーと各アナライザーに対するすべての設定は復元され、そのプロジェクト用の任意の開発者のマシンで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-117">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="6c7f2-118">Roslyn ベースのアナライザーのユーザー エクスペリエンスは、FxCop の旧バージョンのようなコード分析ライブラリや、セキュリティ分析ツールとは異なるものです。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-118">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="6c7f2-119">明示的に Roslyn ベースのアナライザーを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-119">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="6c7f2-120">Visual Studio の [分析] メニューで [コード分析の実行] メニュー項目を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-120">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="6c7f2-121">Roslyn ベースのアナライザーは、ユーザーの作業と同期して実行されます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-121">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="6c7f2-122">特定のアナライザーについての詳細</span><span class="sxs-lookup"><span data-stu-id="6c7f2-122">More information on specific analyzers</span></span>

<span data-ttu-id="6c7f2-123">このセクションでは、次のアナライザーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-123">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="6c7f2-124">[API アナライザー](api-analyzer.md): このアナライザーでは、コードの互換性の潜在的リスクや、非推奨の API の使用が調べられます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-124">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="6c7f2-125">[フレームワーク アナライザー](framework-analyzer.md): このアナライザーでは、コードが .NET Framework アプリケーションのガイドラインに従っているかどうかが調べられます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-125">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="6c7f2-126">これらの規則には、セキュリティに基づく推奨事項がいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="6c7f2-126">These rules include several security-based recommendations.</span></span>
