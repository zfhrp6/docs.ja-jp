---
title: "Get UI Automation Element Properties | Microsoft Docs"
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
  - "properties, retrieving"
  - "UI Automation, retrieving properties of elements"
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
caps.latest.revision: 5
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 5
---
# Get UI Automation Element Properties
> [!NOTE]
>  このドキュメントは、<xref:System.Windows.Automation> 名前空間で定義されているマネージ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クラスを使用する .NET Framework 開発者を対象としています。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に関する最新情報については、「[Windows Automation API: UI Automation \(Windows オートメーション API: UI オートメーション\)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 ここでは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]要素のプロパティを取得する方法について説明します。  
  
### 現在のプロパティ値の取得  
  
1.  取得するプロパティを持つ <xref:System.Windows.Automation.AutomationElement> を取得します。  
  
2.  <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> を呼び出すか、または <xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。  
  
### キャッシュされたプロパティ値の取得  
  
1.  取得するプロパティを持つ <xref:System.Windows.Automation.AutomationElement> を取得します。  プロパティは、<xref:System.Windows.Automation.CacheRequest> で指定されている必要があります。  
  
2.  <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> を呼び出すか、または <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ構造体を取得し、そのメンバーの 1 つから値を取得します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Automation.AutomationElement> の現在のプロパティを取得するためのさまざまな方法を示します。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## 参照  
 [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)   
 [Use Caching in UI Automation](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)   
 [Caching in UI Automation Clients](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)