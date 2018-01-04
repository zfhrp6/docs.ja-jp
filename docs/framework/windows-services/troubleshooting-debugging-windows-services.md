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
ms.workload: dotnet
ms.openlocfilehash: f38e65e93d4e6668795bf254573993d5100e2328
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-debugging-windows-services"></a>Windows サービスをデバッグする場合
Windows サービス アプリケーション、サービスをデバッグする場合に、 **Windows サービス マネージャー**対話します。 **Service Manager**を呼び出して、サービスを開始、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド、および、30 秒間の待機時間、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>を返すメソッド。 この時点で、メソッドが返されない場合、マネージャーは、サービスを開始することはできません、エラーを表示します。  
  
 デバッグする場合に、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド」の説明に従って[する方法: Windows サービス アプリケーションのデバッグ](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)30 秒間のこのを認識する必要があります。 ブレークポイントを配置する場合、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッドと 30 秒以内にしていないステップは、管理者は、サービスを開始していません。  
  
## <a name="see-also"></a>参照  
 [方法 : Windows サービス アプリケーションをデバッグする](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
