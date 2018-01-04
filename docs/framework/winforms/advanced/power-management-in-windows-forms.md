---
title: "Windows フォームでの電源管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7600ae42194b3333c404d217c2605a226df99e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="ca987-102">Windows フォームでの電源管理</span><span class="sxs-lookup"><span data-stu-id="ca987-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="ca987-103">Windows フォーム アプリケーションを利用、電源管理機能の Windows オペレーティング システムにできます。</span><span class="sxs-lookup"><span data-stu-id="ca987-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="ca987-104">アプリケーションでは、コンピューターの電源の状態を監視でき、状態の変更が発生したときにアクションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="ca987-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="ca987-105">たとえば、アプリがポータブル コンピューターで実行されている場合可能性がある、コンピューターのバッテリ充電量が一定のレベルを下回ったときに、アプリケーションで特定の機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="ca987-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="ca987-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供、<xref:Microsoft.Win32.SystemEvents.PowerModeChanged>電源の状態、または AC 電源の状態またはバッテリの状態が変更されたときにユーザーを中断またはオペレーティング システムを再開する場合などに変更があるときに発生するイベントです。</span><span class="sxs-lookup"><span data-stu-id="ca987-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="ca987-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>のプロパティ、<xref:System.Windows.Forms.SystemInformation>できるクラスは次のコード例に示すように現在の状態では、クエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ca987-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="ca987-108">以外にも、<xref:System.Windows.Forms.BatteryChargeStatus>列挙型、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>プロパティには、バッテリ容量を決定するための列挙型も含まれています (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) およびバッテリの充電の割合 (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、 <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>)。</span><span class="sxs-lookup"><span data-stu-id="ca987-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="ca987-109">使用することができます、<xref:System.Windows.Forms.Application.SetSuspendState%2A>のメソッド、<xref:System.Windows.Forms.Application>コンピューターを休止状態または中断モードにします。</span><span class="sxs-lookup"><span data-stu-id="ca987-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="ca987-110">場合、`force`に設定されている引数`false`、オペレーティング システムが中断するアクセス許可を要求するすべてのアプリケーションにイベントをブロードキャストします。</span><span class="sxs-lookup"><span data-stu-id="ca987-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="ca987-111">場合、`disableWakeEvent`に設定されている引数`true`、オペレーティング システムのスリープ解除のすべてのイベントを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ca987-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="ca987-112">次のコード例では、コンピューターを休止状態にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ca987-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ca987-113">参照</span><span class="sxs-lookup"><span data-stu-id="ca987-113">See Also</span></span>  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>  
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>  
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>  
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
