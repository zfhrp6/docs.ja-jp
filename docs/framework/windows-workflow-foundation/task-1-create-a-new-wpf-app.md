---
title: "タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a207b09ff7124bb161678627f365a6fa4021a38d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="b563c-102">タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="b563c-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>
<span data-ttu-id="b563c-103">このタスクでは、WPF Application Visual Studio テンプレートを使用して空の [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] アプリケーションを作成し、適切な [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフロー アセンブリに参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b563c-103">In this task, you will create an empty [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
### <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="b563c-104">WPF アプリケーション プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="b563c-104">To create the WPF Application project</span></span>  
  
1.  <span data-ttu-id="b563c-105">開いている[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]し、**ファイル** メニューのをポイント**新規**、順にクリック**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="b563c-105">Open [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] and on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="b563c-106">**新しいプロジェクト** ダイアログ ボックスで、いずれかを選択**Visual c#**または**Visual Basic**から、**インストールされたテンプレート**の左側にあるウィンドウボックス。</span><span class="sxs-lookup"><span data-stu-id="b563c-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="b563c-107">任意の言語が表示されない場合は、下にある検索**他の言語**します。</span><span class="sxs-lookup"><span data-stu-id="b563c-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>  
  
3.  <span data-ttu-id="b563c-108">選択**Windows**で、**インストールされたテンプレート**ウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="b563c-108">Select **Windows** in the **Installed Templates** pane.</span></span>  
  
4.  <span data-ttu-id="b563c-109">上部のペインにいることを確認 (既定値) **.NET Framework 4**が選択されてドロップダウン リスト ボックスで、 **WPF アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="b563c-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="b563c-110">プロジェクトの名前を設定**HostingApplication**ウィンドウの下部にあります。</span><span class="sxs-lookup"><span data-stu-id="b563c-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>  
  
6.  <span data-ttu-id="b563c-111">ソリューション名を設定します**RehostingTheDesigner**です。</span><span class="sxs-lookup"><span data-stu-id="b563c-111">Set the solution name to **RehostingTheDesigner**.</span></span>  
  
7.  <span data-ttu-id="b563c-112">をクリックして**OK**アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b563c-112">Click **OK** to create the application project.</span></span> [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]<span data-ttu-id="b563c-113"> によって、使用するアプリケーション用の基本的な WPF UI が作成され、適切な XAML と分離コード ファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b563c-113"> creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>  
  
8.  <span data-ttu-id="b563c-114">参照を追加**WorkflowModel**アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="b563c-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="b563c-115">これを行うで**ソリューション エクスプ ローラー**を右クリックし、 **HostingApplication**プロジェクトし、選択**参照の追加**です。</span><span class="sxs-lookup"><span data-stu-id="b563c-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>  
  
9. <span data-ttu-id="b563c-116">**参照の追加**ダイアログ ボックスで、をクリックして、 **.NET**  タブ、CTRL キーを押しながら、次のアセンブリを選択し、をクリックして**OK**:</span><span class="sxs-lookup"><span data-stu-id="b563c-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>  
  
    -   <span data-ttu-id="b563c-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="b563c-117">System.Activities</span></span>  
  
    -   <span data-ttu-id="b563c-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="b563c-118">System.Activities.Presentation</span></span>  
  
    -   <span data-ttu-id="b563c-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="b563c-119">System.Activities.Core.Presentation</span></span>  
  
10. <span data-ttu-id="b563c-120">**[OK]**をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b563c-120">Click **OK**.</span></span>  
  
11. <span data-ttu-id="b563c-121">参照してください[タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)をワークフロー デザイナーのデザイン キャンバスをホストする方法を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b563c-121">See [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b563c-122">参照</span><span class="sxs-lookup"><span data-stu-id="b563c-122">See Also</span></span>  
 [<span data-ttu-id="b563c-123">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="b563c-123">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="b563c-124">タスク 2: ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="b563c-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
