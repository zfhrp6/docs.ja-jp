---
title: "方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 23a1d8c638b198c31d7c83aaf3f216b465f01453
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="b4283-102">方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする</span><span class="sxs-lookup"><span data-stu-id="b4283-102">How to: Install an Assembly into the Global Assembly Cache</span></span>
<span data-ttu-id="b4283-103">厳密な名前付きのアセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b4283-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC):</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b4283-104">GAC にインストールできるのは、厳密な名前付きのアセンブリだけです。</span><span class="sxs-lookup"><span data-stu-id="b4283-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="b4283-105">厳密な名前付きのアセンブリを作成する方法については、「[方法: 厳密な名前でアセンブリに署名する](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4283-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
-   <span data-ttu-id="b4283-106">[Windows インストーラー](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)を使用する。</span><span class="sxs-lookup"><span data-stu-id="b4283-106">Using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span>  
  
     <span data-ttu-id="b4283-107">この操作を行うには、Visual Studio 2012 および Visual Studio 2013 で、InstallShield Limited Edition プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4283-107">You do this in Visual Studio 2012 and Visual Studio 2013 by creating an InstallShield Limited Edition Project.</span></span>  
  
     <span data-ttu-id="b4283-108">これは、アセンブリをグローバル アセンブリ キャッシュに追加する最も一般的な方法です。この方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b4283-108">This is the recommended and most common way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="b4283-109">このインストーラーを使用すると、グローバル アセンブリ キャッシュ内のアセンブリの参照カウントが示されるなどの利点があります。</span><span class="sxs-lookup"><span data-stu-id="b4283-109">The installer provides reference counting of assemblies in the global assembly cache, plus other benefits.</span></span>  
  
-   <span data-ttu-id="b4283-110">[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用する。</span><span class="sxs-lookup"><span data-stu-id="b4283-110">Using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
     <span data-ttu-id="b4283-111">Gacutil.exe を使用すると、厳密な名前付きアセンブリをグローバル アセンブリ キャッシュに追加したり、グローバル アセンブリ キャッシュの内容を表示したりできます。</span><span class="sxs-lookup"><span data-stu-id="b4283-111">You can use Gacutil.exe to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b4283-112">Gacutil.exe は開発専用です。製品アセンブリをグローバル アセンブリ キャッシュにインストールするためには使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b4283-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4283-113">以前のバージョンの .NET Framework では、Windows のシェル拡張機能である Shfusion.dll により、エクスプローラーでアセンブリをドラッグしてインストールすることができました。</span><span class="sxs-lookup"><span data-stu-id="b4283-113">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in File Explorer.</span></span> <span data-ttu-id="b4283-114">[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="b4283-114">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a><span data-ttu-id="b4283-115">グローバル アセンブリ キャッシュ ツール (Gacutil.exe) を使用するには</span><span class="sxs-lookup"><span data-stu-id="b4283-115">To use the Global Assembly Cache tool (Gacutil.exe)</span></span>  
  
1.  <span data-ttu-id="b4283-116">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="b4283-116">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b4283-117">**gacutil -i** \<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="b4283-117">**gacutil -i** \<*assembly name*></span></span>  
  
     <span data-ttu-id="b4283-118">このコマンドで、*assembly name* はグローバル アセンブリ キャッシュにインストールされるアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="b4283-118">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>  
  
 <span data-ttu-id="b4283-119">ファイル名 `hello.dll` のアセンブリをグローバル アセンブリ キャッシュにインストールする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b4283-119">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>  
  
```  
gacutil -i hello.dll  
```  
  
 <span data-ttu-id="b4283-120">詳細については、「[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4283-120">For more information, see [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
### <a name="to-use-an-installshield-limited-edition-project"></a><span data-ttu-id="b4283-121">InstallShield Limited Edition プロジェクトを使用するには</span><span class="sxs-lookup"><span data-stu-id="b4283-121">To use an InstallShield Limited Edition Project</span></span>  
  
1.  <span data-ttu-id="b4283-122">ソリューションのショートカット メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択して、ソリューションにセットアップと配置パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="b4283-122">Add a setup and deployment package to your solution by opening the shortcut menu for your solution, and then choosing **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="b4283-123">**[新しいプロジェクトの追加]** ダイアログ ボックスの **[インストール済み]** フォルダーで、**[その他のプロジェクトの種類]**、**[セットアップと配置]**、**[InstallShield Limited Edition]** の順に選択し、プロジェクトに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="b4283-123">In the **Add New Project** dialog box, in the **Installed** folder, choose **Other Project Types**,  **Setup and Deployment**, **InstallShield Limited Edition**, and give your project a name.</span></span> <span data-ttu-id="b4283-124">(プロンプトが表示されたら、InstallShield をダウンロードし、インストールしてアクティブにします。)</span><span class="sxs-lookup"><span data-stu-id="b4283-124">(If prompted, download, install, and activate InstallShield.)</span></span>  
  
3.  <span data-ttu-id="b4283-125">**ソリューション エクスプローラー**のプロジェクト アシスタントを使用するか、**ソリューション エクスプローラー**の番号付き手順のサブ手順を選択して、セットアップと配置プロジェクトの一般的な構成を行います。アセンブリを GAC に追加しない場合と同様にセットアップを構成します。</span><span class="sxs-lookup"><span data-stu-id="b4283-125">Perform the general configuration of your setup and deployment project either by using the Project Assistant in **Solution Explorer**, or by choosing the substeps of the numbered steps in the **Solution Explorer**.Configure your setup as you would if you were not adding assemblies to the GAC.</span></span>  
  
4.  <span data-ttu-id="b4283-126">アセンブリを GAC に追加するプロセスを開始するには、**ソリューション エクスプローラー**の **[アプリケーション データの指定]** 手順の下にある **[ファイル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4283-126">To begin the process of adding an assembly to the GAC, choose **Files**, which is under the **Specify Application Data** step in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="b4283-127">**[インストール先コンピューターのフォルダー]** ペインで、**[インストール先コンピューター]** のショートカット メニューを開き、**[定義済みフォルダーの表示]**、**[GlobalAssemblyCache]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="b4283-127">In the **Destination computer's folders** pane, open the shortcut menu for **Destination Computer**, and then choose **Show Predefined Folder**, **[GlobalAssemblyCache]**.</span></span>  
  
6.  <span data-ttu-id="b4283-128">グローバル アセンブリ キャッシュにインストールするアセンブリを含む、ソリューション内の各プロジェクトで、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="b4283-128">For each project in the solution that contains an assembly that you want to install in the global assembly cache:</span></span>  
  
    1.  <span data-ttu-id="b4283-129">**[インストール元コンピューターのフォルダー]** ペインでプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="b4283-129">In the **Source computer's folders** pane, choose the project.</span></span>  
  
    2.  <span data-ttu-id="b4283-130">**[インストール先コンピューターのフォルダー]** ペインで **[GlobalAssemblyCache]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4283-130">In the **Destination computer's folders** pane, choose **[GlobalAssemblyCache]**.</span></span>  
  
    3.  <span data-ttu-id="b4283-131">**[インストール元コンピューターのファイル]** ペインで、**[*<project_name>* のプライマリ出力]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b4283-131">In the **Source computer's files** pane, choose **Primary output from** *<project_name>*.</span></span>  
  
    4.  <span data-ttu-id="b4283-132">手順 c のファイルを **[インストール先コンピューターのファイル]** ペインにドラッグします (または、ファイルのショートカット メニューの **[コピー]** と **[貼り付け]** コマンドを使用します)。</span><span class="sxs-lookup"><span data-stu-id="b4283-132">Drag the file in step c to the **Destination computer's files** pane (or use the **Copy** and **Paste** commands from the file's shortcut menu).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4283-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4283-133">See Also</span></span>  
 [<span data-ttu-id="b4283-134">アセンブリとグローバル アセンブリ キャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="b4283-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="b4283-135">方法: グローバル アセンブリ キャッシュからアセンブリを削除する</span><span class="sxs-lookup"><span data-stu-id="b4283-135">How to: Remove an Assembly from the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [<span data-ttu-id="b4283-136">Gacutil.exe (グローバル アセンブリ キャッシュ ツール)</span><span class="sxs-lookup"><span data-stu-id="b4283-136">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="b4283-137">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="b4283-137">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [<span data-ttu-id="b4283-138">Windows インストーラーの配置</span><span class="sxs-lookup"><span data-stu-id="b4283-138">Windows Installer Deployment</span></span>](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
