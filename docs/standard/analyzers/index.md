---
title: Roslyn ベースのアナライザー - .NET
description: 問題を検出し、各問題について修正を提案する Roslyn ベースのアナライザーについて説明します。
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ec153b8fed08ef245a3a0f58970b4e3955dfacb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="the-roslyn-based-analyzers"></a><span data-ttu-id="bc755-103">Roslyn ベースのアナライザー</span><span class="sxs-lookup"><span data-stu-id="bc755-103">The Roslyn based Analyzers</span></span>

<span data-ttu-id="bc755-104">Roslyn ベースのアナライザーでは、.NET Compiler SDK (Roslyn の API) を使用して、プロジェクトのソース コードを分析し、問題の検出と修正の提案を行います。</span><span class="sxs-lookup"><span data-stu-id="bc755-104">Roslyn-based analyzers use the .NET Compiler SDK (Roslyn APIs) to analyze your project's source code to find issues and suggest corrections.</span></span> <span data-ttu-id="bc755-105">検出する問題のクラスは、バグを起こしやすい慣習から API の互換性に関するセキュリティの問題まで、アナライザーによってさまざまです。</span><span class="sxs-lookup"><span data-stu-id="bc755-105">Different analyzers look for different classes of issues, ranging from practices that are likely to cause bugs to security concerns to API compatibility.</span></span>

<span data-ttu-id="bc755-106">Roslyn ベースのアナライザーは対話型であり、ビルド中にも動作します。</span><span class="sxs-lookup"><span data-stu-id="bc755-106">Roslyn-based analyzers work both interactively and during builds.</span></span> <span data-ttu-id="bc755-107">Visual Studio またはコマンド ラインからビルドする際に、アナライザーはさまざまなガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bc755-107">The analyzer provides different guidance when in Visual Studio or in command-line builds.</span></span>

<span data-ttu-id="bc755-108">Visual Studio でコードを編集する場合、コードを変更するとアナライザーが実行され、問題を含むコードの作成後すぐに考えられる問題がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="bc755-108">While you edit code in Visual Studio, the analyzers run as you make changes, catching possible issues as soon as you create code that trigger concerns.</span></span> <span data-ttu-id="bc755-109">すべての問題は波線で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-109">Any issues are highlighted with squiggles under any issue.</span></span> <span data-ttu-id="bc755-110">Visual Studio に表示される電球をクリックすると、その問題に対して考えられる修正方法がアナライザーによって提案されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-110">Visual Studio displays a light bulb, and when you click on it the analyzer will suggest possible fixes for that issue.</span></span> <span data-ttu-id="bc755-111">Visual Studio またはコマンド ラインでプロジェクトをビルドすると、すべてのソース コードが分析され、潜在的な問題の全リストがアナライザーによって示されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-111">When you build the project, either in Visual Studio or from the command line, all the source code is analyzed and the analyzer provides a full list of potential issues.</span></span> <span data-ttu-id="bc755-112">次の図に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bc755-112">The following figure shows one example.</span></span>

![フレームワーク アナライザーによって報告される問題](./media/framework-analyzers-2.png)

<span data-ttu-id="bc755-114">Roslyn ベースのアナライザーでは、エラー、警告、または問題の重大度に基づく情報として、潜在的な問題が報告されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-114">Roslyn-based analyzers report potential issues as errors, warnings, or information based on the severity of the issue.</span></span>

<span data-ttu-id="bc755-115">Roslyn ベースのアナライザーは、プロジェクト内に NuGet パッケージとしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="bc755-115">You install Roslyn-based analyzers as NuGet packages in your project.</span></span> <span data-ttu-id="bc755-116">構成されたアナライザーと各アナライザーに対するすべての設定は復元され、そのプロジェクト用の任意の開発者のマシンで実行されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-116">The configured analyzers and any settings for each analyzer are restored and run on any developer's machine for that project.</span></span>

> [!NOTE]
> <span data-ttu-id="bc755-117">Roslyn ベースのアナライザーのユーザー エクスペリエンスは、FxCop の旧バージョンのようなコード分析ライブラリや、セキュリティ分析ツールとは異なるものです。</span><span class="sxs-lookup"><span data-stu-id="bc755-117">The user experience for Roslyn-based analyzers is different than that of the Code Analysis libraries like the older versions of FxCop and the security analysis tools.</span></span>  <span data-ttu-id="bc755-118">明示的に Roslyn ベースのアナライザーを実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bc755-118">You don't need to explicitly run the Roslyn-based analyzers.</span></span> <span data-ttu-id="bc755-119">Visual Studio の [分析] メニューで [コード分析の実行] メニュー項目を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bc755-119">There's no need to use the "Run Code Analysis" menu items on the "Analyze" menu in Visual Studio.</span></span> <span data-ttu-id="bc755-120">Roslyn ベースのアナライザーは、ユーザーの作業と同期して実行されます。</span><span class="sxs-lookup"><span data-stu-id="bc755-120">Roslyn-based analyzers run asychronously as you work.</span></span> 

## <a name="more-information-on-specific-analyzers"></a><span data-ttu-id="bc755-121">特定のアナライザーについての詳細</span><span class="sxs-lookup"><span data-stu-id="bc755-121">More information on specific analyzers</span></span>

<span data-ttu-id="bc755-122">このセクションでは、次のアナライザーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bc755-122">The following analyzers are covered in this section:</span></span>

<span data-ttu-id="bc755-123">[API アナライザー](api-analyzer.md): このアナライザーでは、コードの互換性の潜在的リスクや、非推奨の API の使用が調べられます。</span><span class="sxs-lookup"><span data-stu-id="bc755-123">[API Analyzer](api-analyzer.md): This analyzer examines your code for potential compatibility risks or uses of deprecated APIs.</span></span>    
<span data-ttu-id="bc755-124">[フレームワーク アナライザー](framework-analyzer.md): このアナライザーでは、コードが .NET Framework アプリケーションのガイドラインに従っているかどうかが調べられます。</span><span class="sxs-lookup"><span data-stu-id="bc755-124">[Framework Analyzer](framework-analyzer.md): This analyzer examines your code to ensure it follows the guidelines for .NET Framework applications.</span></span> <span data-ttu-id="bc755-125">これらの規則には、セキュリティに基づく推奨事項がいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="bc755-125">These rules include several security-based recommendations.</span></span>
