---
title: "方法: Windows サービスを続行する (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Continue
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: e5d13760-4c83-4b0d-abef-39852677cd7a
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 73b16a5e5834f7279ae551d4e7efd26cc86c1d07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-continue-a-windows-service-visual-basic"></a><span data-ttu-id="65ff5-102">方法: Windows サービスを続行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65ff5-102">How to: Continue a Windows Service (Visual Basic)</span></span>
<span data-ttu-id="65ff5-103">この例では、<xref:System.ServiceProcess.ServiceController>コンポーネントをローカル コンピューターで、IIS Admin サービスを続行します。</span><span class="sxs-lookup"><span data-stu-id="65ff5-103">This example uses the <xref:System.ServiceProcess.ServiceController> component to continue the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65ff5-104">例</span><span class="sxs-lookup"><span data-stu-id="65ff5-104">Example</span></span>  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#13](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#13)]  
  
 <span data-ttu-id="65ff5-105">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="65ff5-105">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="65ff5-106">配置されているコード スニペット ピッカーで**Windows オペレーティング システム > Windows サービス**です。</span><span class="sxs-lookup"><span data-stu-id="65ff5-106">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="65ff5-107">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65ff5-107">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="65ff5-108">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="65ff5-108">Compiling the Code</span></span>  
 <span data-ttu-id="65ff5-109">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="65ff5-109">This example requires:</span></span>  
  
-   <span data-ttu-id="65ff5-110">System.serviceprocess.dll へのプロジェクト参照。</span><span class="sxs-lookup"><span data-stu-id="65ff5-110">A project reference to System.serviceprocess.dll.</span></span>  
  
-   <span data-ttu-id="65ff5-111"><xref:System.ServiceProcess> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="65ff5-111">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="65ff5-112">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="65ff5-112">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="65ff5-113">詳細については、「[Imports ステートメント (.NET 名前空間および型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65ff5-113">For more information, see [Imports Statement (.NET Namespace and Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="65ff5-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="65ff5-114">Robust Programming</span></span>  
 <span data-ttu-id="65ff5-115"><xref:System.ServiceProcess.ServiceController.MachineName%2A>のプロパティ、<xref:System.ServiceProcess.ServiceController>クラスは既定では、ローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="65ff5-115">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="65ff5-116">別のコンピューターで Windows サービスを参照するには、変更、<xref:System.ServiceProcess.ServiceController.MachineName%2A>プロパティをそのコンピューターの名前にします。</span><span class="sxs-lookup"><span data-stu-id="65ff5-116">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="65ff5-117">呼び出すことはできません、<xref:System.ServiceProcess.ServiceController.Continue%2A>サービス コント ローラーの状態になるまで、サービスに対してメソッド<xref:System.ServiceProcess.ServiceControllerStatus.Paused>です。</span><span class="sxs-lookup"><span data-stu-id="65ff5-117">You cannot call the <xref:System.ServiceProcess.ServiceController.Continue%2A> method on a service until the service controller status is <xref:System.ServiceProcess.ServiceControllerStatus.Paused>.</span></span>  
  
 <span data-ttu-id="65ff5-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65ff5-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="65ff5-119">サービスを再開することはできません。</span><span class="sxs-lookup"><span data-stu-id="65ff5-119">The service cannot be resumed.</span></span> <span data-ttu-id="65ff5-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="65ff5-120">(<xref:System.InvalidOperationException>)</span></span>  
  
-   <span data-ttu-id="65ff5-121">システム API にアクセス中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="65ff5-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="65ff5-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="65ff5-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="65ff5-123">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="65ff5-123">.NET Framework Security</span></span>  
 <span data-ttu-id="65ff5-124">使用して、コンピューター上のサービスのコントロールを制限できる、<xref:System.ServiceProcess.ServiceControllerPermissionAccess>列挙型のアクセス許可設定を<xref:System.ServiceProcess.ServiceControllerPermission>クラスです。</span><span class="sxs-lookup"><span data-stu-id="65ff5-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> enumeration to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission> class.</span></span>  
  
 <span data-ttu-id="65ff5-125">使用してサービスの情報へのアクセスを制限することがあります、<xref:System.Security.Permissions.PermissionState>列挙型のアクセス許可設定を<xref:System.Security.Permissions.SecurityPermission>クラスです。</span><span class="sxs-lookup"><span data-stu-id="65ff5-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> enumeration to set permissions in the <xref:System.Security.Permissions.SecurityPermission> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ff5-126">参照</span><span class="sxs-lookup"><span data-stu-id="65ff5-126">See Also</span></span>  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 [<span data-ttu-id="65ff5-127">方法 : Windows サービスを一時中断する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65ff5-127">How to: Pause a Windows Service (Visual Basic)</span></span>](../../../docs/framework/windows-services/how-to-pause-a-windows-service-visual-basic.md)
