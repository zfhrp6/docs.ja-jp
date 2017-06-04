---
title: "Get the Toggle State of a Check Box Using UI Automation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI Automation, getting toggle states of check boxes"
  - "check boxes, getting toggle states of"
  - "getting, toggle states of check boxes"
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
caps.latest.revision: 10
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 10
---
# Get the Toggle State of a Check Box Using UI Automation
> [!NOTE]
>  このドキュメントは、<xref:System.Windows.Automation> 名前空間で定義されているマネージ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クラスを使用する .NET Framework 開発者を対象としています。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に関する最新情報については、「[Windows Automation API: UI Automation \(Windows オートメーション API: UI オートメーション\)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 ここでは、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]を使用してコントロールのトグル状態を取得する方法を示します。  
  
## 使用例  
 この例では、<xref:System.Windows.Automation.AutomationElement> クラスの <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> メソッドを使用して、コントロールから <xref:System.Windows.Automation.TogglePattern> オブジェクトを取得し、その <xref:System.Windows.Automation.ToggleState> プロパティを返します。  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]