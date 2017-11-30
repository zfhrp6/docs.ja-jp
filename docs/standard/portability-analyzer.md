---
title: ".NET 移植性アナライザー - .NET"
description: ".NET Portability Analyzer ツールを使用して、さまざまな .NET 実装間で、コードの移植性を評価する方法について説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/26/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: c204af75283278d16bf661e76f2ec5ae0f1d0b3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="88f82-104">.NET Portability Analyzer</span><span class="sxs-lookup"><span data-stu-id="88f82-104">The .NET Portability Analyzer</span></span>

<span data-ttu-id="88f82-105">ライブラリをマルチプラットフォーム対応にしたい場合や、</span><span class="sxs-lookup"><span data-stu-id="88f82-105">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="88f82-106">アプリケーションで他の .NET 実装との互換性を確保するのに必要な作業量を知りたい場合は、</span><span class="sxs-lookup"><span data-stu-id="88f82-106">Want to see how much work is required to make your application compatible with other .NET implementations?</span></span> <span data-ttu-id="88f82-107">[.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) が役立ちます。このツールを使用すると、アセンブリを分析して、プログラムが .NET 実装全体でどの程度柔軟な構造になっているかについて詳細なレポートを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="88f82-107">The [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="88f82-108">Portability Analyzer は、Visual Studio 拡張機能のコンソール アプリとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="88f82-108">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="88f82-109">新しいターゲット</span><span class="sxs-lookup"><span data-stu-id="88f82-109">New targets</span></span>

* <span data-ttu-id="88f82-110">[.NET Core](https://dotnetfoundation.org/net-core): モジュール型の設計で、side-by-side を採用しており、クロスプラットフォームのシナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="88f82-110">[.NET Core](https://dotnetfoundation.org/net-core): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="88f82-111">side-by-side 機能により、他のアプリに影響を与えることなく新しい .NET Core バージョンを導入することができます。</span><span class="sxs-lookup"><span data-stu-id="88f82-111">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="88f82-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core): .NET Core 上に構築された最新の Web フレームワークであり、開発者に .NET Core と同じメリットを提供します。</span><span class="sxs-lookup"><span data-stu-id="88f82-112">[ASP.NET Core](https://dotnetfoundation.org/asp-net-core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="88f82-113">[ユニバーサル Windows プラットフォーム](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): .NET Native の静的コンパイルを使用することで、x64 および ARM マシンで動作する Windows ストア アプリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="88f82-113">[Universal Windows Platform](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="88f82-114">.NET Core + プラットフォーム拡張機能: .NET Core API と、WCF、ASP.NET Core、FSharp、Azure などの .NET エコシステム内のその他の API が含まれます。</span><span class="sxs-lookup"><span data-stu-id="88f82-114">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="88f82-115">.NET Standard + プラットフォーム拡張機能: .NET Standard API と、WCF、ASP.NET Core、FSharp、および Azure などの .NET エコシステム内のその他の API が含まれます。</span><span class="sxs-lookup"><span data-stu-id="88f82-115">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-portability-analyzer"></a><span data-ttu-id="88f82-116">Portability Analyzer の使用方法</span><span class="sxs-lookup"><span data-stu-id="88f82-116">How to use Portability Analyzer</span></span>

<span data-ttu-id="88f82-117">.NET Portability Analyzer を使用するには、[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=507467)から拡張機能をダウンロードし、インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="88f82-117">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Gallery](http://go.microsoft.com/fwlink/?LinkID=507467).</span></span> <span data-ttu-id="88f82-118">これは、Visual Studio 2015 と Visual Studio 2017 で機能します。</span><span class="sxs-lookup"><span data-stu-id="88f82-118">It works on Visual Studio 2015 and Visual Studio 2017.</span></span> <span data-ttu-id="88f82-119">**[分析]**、 > **[Portability Analyzer Settings (Portability Analyzer の設定)]** の順に選択して構成し、ターゲット プラットフォームを選択できます。</span><span class="sxs-lookup"><span data-stu-id="88f82-119">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![Portability のスクリーンショット](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="88f82-121">プロジェクト全体を分析するには、**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[Analyze Assembly Portability]** (アセンブリの移植性を分析) を選択します。</span><span class="sxs-lookup"><span data-stu-id="88f82-121">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="88f82-122">または、**[分析]** メニューで **[Analyze Assembly Portability]** (アセンブリの移植性を分析) を選択します。</span><span class="sxs-lookup"><span data-stu-id="88f82-122">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="88f82-123">そこから、プロジェクトの実行可能ファイルまたは DLL を選択します。</span><span class="sxs-lookup"><span data-stu-id="88f82-123">From there, select your project’s executable or DLL.</span></span>

![移植性ソリューション エクスプローラー](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="88f82-125">分析を実行すると、.NET 移植性レポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="88f82-125">After running the analysis, you will see your .NET Portability Report.</span></span> <span data-ttu-id="88f82-126">ターゲット プラットフォームでサポートされていない型のみが一覧に表示され、**[エラー一覧]** の **[メッセージ]** タブで、推奨事項を確認できます。</span><span class="sxs-lookup"><span data-stu-id="88f82-126">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="88f82-127">また、**[メッセージ]** タブから問題のある領域に直接移動することもできます。</span><span class="sxs-lookup"><span data-stu-id="88f82-127">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![移植性レポート](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="88f82-129">Visual Studio を使用しない場合は、</span><span class="sxs-lookup"><span data-stu-id="88f82-129">Don’t want to use Visual Studio?</span></span> <span data-ttu-id="88f82-130">コマンド プロンプトから Portability Analyzer を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="88f82-130">You can also use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="88f82-131">[API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="88f82-131">Just download the [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678).</span></span>

*   <span data-ttu-id="88f82-132">現在のディレクトリを分析するには、次のコマンドを入力します。`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="88f82-132">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
*   <span data-ttu-id="88f82-133">特定の .dll ファイルの一覧を分析するには、次のコマンドを入力します。`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="88f82-133">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="88f82-134">.NET 移植性レポートは、Excel ファイル (*.xlsx*) として現在のディレクトリに保存されます。</span><span class="sxs-lookup"><span data-stu-id="88f82-134">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="88f82-135">Excel のブックの **[詳細]** タブに詳細情報が記載されています。</span><span class="sxs-lookup"><span data-stu-id="88f82-135">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="88f82-136">.NET Portability Analyzer の詳細については、[GitHub ドキュメント](https://github.com/Microsoft/dotnet-apiport#documentation)にアクセスし、Channel 9 動画の「[A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)」 (.NET Portability Analyzer の概要) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="88f82-136">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
