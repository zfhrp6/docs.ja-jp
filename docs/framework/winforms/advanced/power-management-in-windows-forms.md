---
title: "Windows フォームでの電源管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "バッテリ状態"
  - "電源状態"
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Windows フォームでの電源管理
Windows フォーム アプリケーションでは、Windows オペレーティング システムの電源管理機能を利用できます。  コンピューターの電源状態を監視し、状態が変化したときにアクションを実行できます。  たとえば、ポータブル コンピューターでアプリケーションを実行している場合、コンピューターの充電が一定レベルを下回ったときにアプリケーションの特定の機能を無効にできます。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、オペレーティング システムを中断または再開したり、AC 電源やバッテリの状態が変化したりした場合など、電源状態が変化したときに発生する <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> イベントを利用できます。  <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> クラスの <xref:System.Windows.Forms.SystemInformation> プロパティを使用すると、次のコード例に示すように現在の状態を照会できます。  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <xref:System.Windows.Forms.BatteryChargeStatus> 列挙値の他に、<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> プロパティにも、バッテリ容量 \(<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>\)、バッテリの充電率 \(<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、<xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>\) を確認する列挙値が含まれています。  
  
 <xref:System.Windows.Forms.Application> の <xref:System.Windows.Forms.Application.SetSuspendState%2A> メソッドを使用すると、コンピューターを休止モードまたは中断モードに設定できます。  `force` 引数を `false` に設定すると、中断のためのアクセス許可を要求するすべてのアプリケーションにイベントがブロードキャストされます。  また、`disableWakeEvent` 引数を `true` に設定すると、すべての wake イベントが無効になります。  
  
 次のコード例は、コンピューターを休止モードに設定する方法を示しています。  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## 参照  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>   
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>   
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>   
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>