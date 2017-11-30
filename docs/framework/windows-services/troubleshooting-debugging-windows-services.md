---
title: "Windows サービスをデバッグする場合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 51c28f6e9b6fa2974fb9861716b2c9fc2a38fe1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="92342-102">Windows サービスをデバッグする場合</span><span class="sxs-lookup"><span data-stu-id="92342-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="92342-103">Windows サービス アプリケーション、サービスをデバッグする場合に、 **Windows サービス マネージャー**対話します。</span><span class="sxs-lookup"><span data-stu-id="92342-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="92342-104">**Service Manager**を呼び出して、サービスを開始、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド、および、30 秒間の待機時間、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>を返すメソッド。</span><span class="sxs-lookup"><span data-stu-id="92342-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="92342-105">この時点で、メソッドが返されない場合、マネージャーは、サービスを開始することはできません、エラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="92342-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="92342-106">デバッグする場合に、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド」の説明に従って[する方法: Windows サービス アプリケーションのデバッグ](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)30 秒間のこのを認識する必要があります。</span><span class="sxs-lookup"><span data-stu-id="92342-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="92342-107">ブレークポイントを配置する場合、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッドと 30 秒以内にしていないステップは、管理者は、サービスを開始していません。</span><span class="sxs-lookup"><span data-stu-id="92342-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92342-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="92342-108">See Also</span></span>  
 [<span data-ttu-id="92342-109">方法: Windows サービス アプリケーションのデバッグ</span><span class="sxs-lookup"><span data-stu-id="92342-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="92342-110">Windows サービス アプリケーションの概要</span><span class="sxs-lookup"><span data-stu-id="92342-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
