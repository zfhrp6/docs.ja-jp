---
title: Windows サービスをデバッグする場合
ms.date: 03/30/2017
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
author: ghogen
manager: douge
ms.openlocfilehash: 77a0c19c2da2d1886beaf396650fa024fc1243a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-debugging-windows-services"></a>Windows サービスをデバッグする場合
Windows サービス アプリケーション、サービスをデバッグする場合に、 **Windows サービス マネージャー**対話します。 **Service Manager**を呼び出して、サービスを開始、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド、および、30 秒間の待機時間、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>を返すメソッド。 この時点で、メソッドが返されない場合、マネージャーは、サービスを開始することはできません、エラーを表示します。  
  
 デバッグする場合に、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッド」の説明に従って[する方法: Windows サービス アプリケーションのデバッグ](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)30 秒間のこのを認識する必要があります。 ブレークポイントを配置する場合、<xref:System.ServiceProcess.ServiceBase.OnStart%2A>メソッドと 30 秒以内にしていないステップは、管理者は、サービスを開始していません。  
  
## <a name="see-also"></a>関連項目  
 [方法 : Windows サービス アプリケーションをデバッグする](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
