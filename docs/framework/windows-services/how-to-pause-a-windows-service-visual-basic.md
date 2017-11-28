---
title: "方法: Windows サービスを一時中断する (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d44358d3f76f50a06ede5e7d720f4f48d80893de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="102ee-102">方法: Windows サービスを一時中断する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="102ee-102">How to: Pause a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="102ee-103">この例では、<xref:System.ServiceProcess.ServiceController>コンポーネントがローカル コンピューター上の IIS 管理サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="102ee-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="102ee-104">例</span><span class="sxs-lookup"><span data-stu-id="102ee-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="102ee-105">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="102ee-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="102ee-106">配置されているコード スニペット ピッカーで**Windows オペレーティング システム > Windows サービス**です。</span><span class="sxs-lookup"><span data-stu-id="102ee-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="102ee-107">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="102ee-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="102ee-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="102ee-108">Compiling the Code</span></span>  
 <span data-ttu-id="102ee-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="102ee-109">This example requires:</span></span>  
  
-   <span data-ttu-id="102ee-110">System.serviceprocess.dll へのプロジェクト参照。</span><span class="sxs-lookup"><span data-stu-id="102ee-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="102ee-111"><xref:System.ServiceProcess> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="102ee-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="102ee-112">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="102ee-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="102ee-113">詳細については、「[Imports ステートメント (.NET 名前空間および型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="102ee-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="102ee-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="102ee-114">Robust Programming</span></span>  
 <span data-ttu-id="102ee-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A>のプロパティ、<xref:System.ServiceProcess.ServiceController>クラスは既定では、ローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="102ee-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="102ee-116">別のコンピューターで Windows サービスを参照するには、変更、<xref:System.ServiceProcess.ServiceController.MachineName%2A>プロパティをそのコンピューターの名前にします。</span><span class="sxs-lookup"><span data-stu-id="102ee-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="102ee-117">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="102ee-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="102ee-118">サービスを一時停止することはできません。</span><span class="sxs-lookup"><span data-stu-id="102ee-118">The service cannot be paused.</span></span> <span data-ttu-id="102ee-119">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="102ee-119">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="102ee-120">システム API にアクセス中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="102ee-120">An error occurred when accessing a system API.</span></span> <span data-ttu-id="102ee-121">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="102ee-121">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="102ee-122">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="102ee-122">.NET Framework Security</span></span>  
 <span data-ttu-id="102ee-123">使用して、コンピューター上のサービスのコントロールを制限できる、<xref:System.ServiceProcess.ServiceControllerPermissionAccess>アクセス許可を設定、<xref:System.ServiceProcess.ServiceControllerPermission>です。</span><span class="sxs-lookup"><span data-stu-id="102ee-123">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="102ee-124">使用してサービスの情報へのアクセスを制限することがあります、<xref:System.Security.Permissions.PermissionState>アクセス許可を設定、<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="102ee-124">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="102ee-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="102ee-125">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [<span data-ttu-id="102ee-126">方法: Windows サービス (Visual Basic) を続行</span><span class="sxs-lookup"><span data-stu-id="102ee-126">How to: Continue a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
