---
title: "方法 : Visual Studio で LINQ to DataSet プロジェクトを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c749cdd56f0c964b84788b05470406234ef3eb0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="2be37-102">方法 : Visual Studio で LINQ to DataSet プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2be37-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="2be37-103">別の種類の [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プロジェクトでは、特定のインポートされる名前空間 (Visual Basic) または `using` ディレクティブ (C#) および参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="2be37-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="2be37-104">最小要件は、System.Core.dll への参照と、`using` の <xref:System.Linq> ディレクティブです。</span><span class="sxs-lookup"><span data-stu-id="2be37-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="2be37-105">既定では、これらは新しい [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] プロジェクトを作成した場合に提供されます。</span><span class="sxs-lookup"><span data-stu-id="2be37-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> <span data-ttu-id="2be37-106">また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、System.Data.dll および System.Data.DataSetExtensions.dll への参照と、`Imports` (Visual Basic) または `using` (C#) ディレクティブも必要です。</span><span class="sxs-lookup"><span data-stu-id="2be37-106">[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="2be37-107">以前のバージョンの Visual Studio のプロジェクトをアップグレードする場合、これらの LINQ 関連の参照を手動で追加する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2be37-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="2be37-108">さらに、.NET Framework バージョン 3.5 をプロジェクトのターゲットとして手動で設定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2be37-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2be37-109">コマンド プロンプトから構築する場合での LINQ に関連する Dll を手動で参照する必要があります`drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5 です。</span><span class="sxs-lookup"><span data-stu-id="2be37-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="2be37-110">.NET Framework 3.5 をターゲットとして設定するには</span><span class="sxs-lookup"><span data-stu-id="2be37-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="2be37-111">[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] で、新しい Visual Basic または C# プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="2be37-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="2be37-112">または、Visual Studio 2005 で作成されている Visual Basic または C# プロジェクトを開き、指示に従って [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] プロジェクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="2be37-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="2be37-113">C# プロジェクトをクリックして、**プロジェクト** メニューをクリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="2be37-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="2be37-114">**アプリケーション**プロパティ] ページで、[.NET Framework 3.5、**ターゲット フレームワーク**ドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="2be37-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="2be37-115">Visual Basic プロジェクトをクリックして、**プロジェクト** メニューをクリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="2be37-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="2be37-116">**コンパイル**プロパティ ページで、をクリックして**詳細コンパイル オプション**で .NET Framework 3.5 をクリックして、**ターゲット フレームワーク (すべての構成)**ドロップダウン リスト。</span><span class="sxs-lookup"><span data-stu-id="2be37-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="2be37-117">**プロジェクト** メニューのをクリックして**参照の追加**をクリックして、 **.NET**  タブで、下方向にスクロール**System.Core**をクリックし、 をクリックして**Ok**です。</span><span class="sxs-lookup"><span data-stu-id="2be37-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="2be37-118">ソース コード ファイルまたはプロジェクトに `using` の <xref:System.Linq> ディレクティブまたはインポートされる名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="2be37-119">詳細については、次を参照してください。[ディレクティブを使用して](~/docs/csharp/language-reference/keywords/using-directive.md)または[する方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="2be37-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="2be37-120">LINQ to DataSet 機能を有効にするには</span><span class="sxs-lookup"><span data-stu-id="2be37-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="2be37-121">必要に応じて、このトピックの前の方で説明した手順に従って、System.Core.dll への参照および System.Linq の `using` ディレクティブまたはインポートされる名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="2be37-122">C# または Visual Basic の場合をクリックして、**プロジェクト** メニューをクリックして**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="2be37-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="2be37-123">**参照の追加** ダイアログ ボックスをクリックして、 **.NET**タブが前面にない場合。</span><span class="sxs-lookup"><span data-stu-id="2be37-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="2be37-124">下方向にスクロール**System.Data**と**System.Data.DataSetExtensions**にをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2be37-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="2be37-125">クリックして、 **OK**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2be37-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="2be37-126">ソース コード ファイルまたはプロジェクトに `using` の <xref:System.Data> ディレクティブまたはインポートされる名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="2be37-127">詳細については、次を参照してください。[ディレクティブを使用して](~/docs/csharp/language-reference/keywords/using-directive.md)または[する方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)です。</span><span class="sxs-lookup"><span data-stu-id="2be37-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="2be37-128">LINQ to Dataset 機能を使用するために、System.Data.DataSetExtensions.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="2be37-129">System.Data.dll への参照が追加されていない場合はこれを追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="2be37-130">オプションで、データベースにどのように接続するかに合わせて、`using` または `System.Data.Common` の `System.Data.SqlClient` ディレクティブまたはインポートされる名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="2be37-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2be37-131">参照</span><span class="sxs-lookup"><span data-stu-id="2be37-131">See Also</span></span>  
 [<span data-ttu-id="2be37-132">はじめに</span><span class="sxs-lookup"><span data-stu-id="2be37-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="2be37-133">はじめに (LINQ について)</span><span class="sxs-lookup"><span data-stu-id="2be37-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
