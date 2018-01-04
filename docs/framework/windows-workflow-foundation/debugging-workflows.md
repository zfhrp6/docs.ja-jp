---
title: "デバッグのワークフロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 44814be3a21e9c0ca9ba2b09a5309661a939bbdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-workflows"></a><span data-ttu-id="d1332-102">デバッグのワークフロー</span><span class="sxs-lookup"><span data-stu-id="d1332-102">Debugging Workflows</span></span>
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="d1332-103"> には、開発環境から実行中のワークフローをデバッグするオプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d1332-103"> offers several options for debugging running workflows from the development environment.</span></span> <span data-ttu-id="d1332-104">ワークフローは、デザイナー、XAML、およびコードでデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="d1332-104">Workflows can be debugged in the designer, in XAML, and in code.</span></span>  
  
## <a name="debugging-in-the-workflow-designer"></a><span data-ttu-id="d1332-105">ワークフロー デザイナーでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="d1332-105">Debugging in the Workflow Designer</span></span>  
 <span data-ttu-id="d1332-106">アクティビティを強調表示し、キーを押して、ワークフロー デザイナーでアクティビティにブレークポイントを設定することができます**F9**アクティビティのコンテキスト メニューを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1332-106">Breakpoints can be set on activities in the workflow designer by either highlighting the activity and pressing **F9** or by using the activity’s context menu.</span></span> <span data-ttu-id="d1332-107">ワークフロー ホストをデバッグ モードで実行すると、ワークフローの実行は一時停止します。</span><span class="sxs-lookup"><span data-stu-id="d1332-107">Execution of the workflow then breaks when the workflow host is run in debug mode.</span></span> <span data-ttu-id="d1332-108">次のスクリーンショットでは、ワークフローの実行はブレークポイントで一時停止します。</span><span class="sxs-lookup"><span data-stu-id="d1332-108">In the following screenshot, workflow execution is paused at a breakpoint.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d1332-109">[ワークフロー デザイナーにワークフローのデバッグ](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer)です。</span><span class="sxs-lookup"><span data-stu-id="d1332-109"> [Debugging Workflows with the Workflow Designer](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).</span></span>  
  
## <a name="debugging-in-xaml"></a><span data-ttu-id="d1332-110">XAML でのデバッグ</span><span class="sxs-lookup"><span data-stu-id="d1332-110">Debugging in XAML</span></span>  
 <span data-ttu-id="d1332-111">デザイナーでワークフローがブレークポイントで一時停止すると、XAML でもワークフローをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="d1332-111">If a workflow has paused at a breakpoint in the designer, the workflow can also be debugged in XAML.</span></span> <span data-ttu-id="d1332-112">XAML での実行ポイントを表示する選択**XAML ビュー**ワークフローの実行が一時停止すると、ワークフロー デザイナーでします。</span><span class="sxs-lookup"><span data-stu-id="d1332-112">To view the point of execution in XAML, select **XAML View** in the workflow designer when workflow execution is paused.</span></span> <span data-ttu-id="d1332-113">デバッグをデザイナーに切り替えるには、ソリューション エクスプローラーからデザイナーでワークフローを開き直します。</span><span class="sxs-lookup"><span data-stu-id="d1332-113">Debugging can be switched back to the designer by re-opening the workflow in the designer from the solution explorer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d1332-114">[する方法: ワークフロー デザイナーで XAML をデバッグ](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer)です。</span><span class="sxs-lookup"><span data-stu-id="d1332-114"> [How to: Debug XAML with the Workflow Designer](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).</span></span>  
  
## <a name="debugging-in-code"></a><span data-ttu-id="d1332-115">コードでのデバッグ</span><span class="sxs-lookup"><span data-stu-id="d1332-115">Debugging in Code</span></span>  
 <span data-ttu-id="d1332-116">コードのブレークポイントは、他の命令型アプリケーションで使用する方法と同様に [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1332-116">Code breakpoints can be used in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the same way that they can be used in other imperative applications.</span></span> <span data-ttu-id="d1332-117">コードのブレークポイントを作成するコード ペインの左マージンをクリックしてまたはキーを押して**F9**カーソル位置にブレークポイントを配置します。</span><span class="sxs-lookup"><span data-stu-id="d1332-117">Click the left margin of the code pane to create a code breakpoint, or press **F9** to place a breakpoint at the cursor location.</span></span>  
  
## <a name="attaching-to-a-workflow-process"></a><span data-ttu-id="d1332-118">ワークフロー プロセスへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="d1332-118">Attaching to a Workflow Process</span></span>  
 <span data-ttu-id="d1332-119">ワークフローのデバッグは、Visual Studio のインフラストラクチャを使用したプロセスへのアタッチもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d1332-119">Workflow debugging also supports using Visual Studio’s infrastructure to attach to a process.</span></span> <span data-ttu-id="d1332-120">そのため、ワークフロー作成者は、Internet Information Services (IIS) 7.0 など異なるホスト環境で実行されているワークフローをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="d1332-120">This enables the workflow author to debug a workflow running in a different host environment such as Internet Information Services (IIS) 7.0.</span></span>  
  
## <a name="remote-debugging"></a><span data-ttu-id="d1332-121">リモート デバッグ</span><span class="sxs-lookup"><span data-stu-id="d1332-121">Remote Debugging</span></span>  
 [!INCLUDE[wf](../../../includes/wf-md.md)]<span data-ttu-id="d1332-122"> のリモート デバッグは、他の [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] コンポーネントのリモート デバッグと同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="d1332-122"> remote debugging functions the same as remote debugging for other [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] components.</span></span> <span data-ttu-id="d1332-123">リモート デバッグの使用方法の詳細については、次を参照してください。[する方法: リモート デバッグを有効にする](http://go.microsoft.com/fwlink/?LinkId=196257)です。</span><span class="sxs-lookup"><span data-stu-id="d1332-123">For information on using remote debugging, see [How to: Enable Remote Debugging](http://go.microsoft.com/fwlink/?LinkId=196257).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1332-124">ワークフロー アプリケーションが x86 を対象とする場合のアーキテクチャが、64 ビットのオペレーティング システムを実行するコンピューターでホストされているリモート デバッグが機能しませんしない限り、および[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)]にインストールされているリモート コンピューターまたはターゲット ワークフロー アプリケーションが変更されました。**任意の CPU**です。</span><span class="sxs-lookup"><span data-stu-id="d1332-124">If the workflow application targets the x86 architecture and is hosted on a computer running a 64 bit operating system, then remote debugging will not work unless [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] is installed on the remote computer or the target for the workflow application is changed to **Any CPU**.</span></span>  
  
## <a name="extending-the-workflow-debugging-service"></a><span data-ttu-id="d1332-125">ワークフロー デバッグ サービスの拡張</span><span class="sxs-lookup"><span data-stu-id="d1332-125">Extending the Workflow Debugging Service</span></span>  
 <span data-ttu-id="d1332-126">ワークフロー デバッガー サービスは公開されるようになり、ホストを変更したデザイナーでのモニタリング、シミュレーション、デバッグなど、カスタム アプリケーションを作成するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1332-126">The workflow debugger service is now public and can be used to create custom applications such as monitoring, simulation, and debugging in a re-hosted designer.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="d1332-127">「<xref:System.Activities.Presentation.Debug.DebuggerService>」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1332-127"> the <xref:System.Activities.Presentation.Debug.DebuggerService> topic.</span></span>
