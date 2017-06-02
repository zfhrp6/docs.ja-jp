---
title: "Find a UI Automation Element Based on a Property Condition | Microsoft Docs"
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
  - "elements, finding by property conditions"
  - "UI Automation, finding elements by property conditions"
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: 19
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 19
---
# Find a UI Automation Element Based on a Property Condition
> [!NOTE]
>  このドキュメントは、<xref:System.Windows.Automation> 名前空間で定義されているマネージ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クラスを使用する .NET Framework 開発者を対象としています。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に関する最新情報については、「[Windows Automation API: UI Automation \(Windows オートメーション API: UI オートメーション\)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックのコード例では、特定のプロパティに基づいて [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内の要素を配置する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Automation.AutomationElement> ツリー内の対象の要素 \(1 つまたは複数\) を識別するプロパティ条件のセットを指定します。  一致するすべての要素の検索は、<xref:System.Windows.Automation.AutomationElement.FindAll%2A> メソッドで実行します。このメソッドでは、組み込まれている一連の <xref:System.Windows.Automation.AndCondition> ブール演算により、一致する要素の数を制限します。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.RootElement%2A> から検索するときは、直接の子だけを取得する必要があります。  子孫を検索すると、要素の処理が数百回または数千回も繰り返される場合があるため、スタック オーバーフローが発生する可能性があります。  低いレベルにある特定の要素を取得する場合は、アプリケーション ウィンドウまたは低いレベルのコンテナーから検索を開始する必要があります。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## 参照  
 [InvokePattern and ExpandCollapsePattern Menu Item Sample](http://msdn.microsoft.com/ja-jp/b7fa141c-e2d1-4da2-a27f-81a7d1172210)   
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)   
 [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md)