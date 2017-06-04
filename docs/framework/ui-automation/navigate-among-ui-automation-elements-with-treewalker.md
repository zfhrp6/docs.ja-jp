---
title: "Navigate Among UI Automation Elements with TreeWalker | Microsoft Docs"
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
  - "classes, TreeWalker"
  - "TreeWalker class"
  - "elements, navigating among"
  - "UI Automation, navigating among elements"
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
caps.latest.revision: 8
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 8
---
# Navigate Among UI Automation Elements with TreeWalker
> [!NOTE]
>  このドキュメントは、<xref:System.Windows.Automation> 名前空間で定義されているマネージ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クラスを使用する .NET Framework 開発者を対象としています。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に関する最新情報については、「[Windows Automation API: UI Automation \(Windows オートメーション API: UI オートメーション\)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックのコード例では、<xref:System.Windows.Automation.TreeWalker> クラスを使用して [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]要素間を移動する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Automation.TreeWalker.GetParent%2A> を使用して、ルート要素であるデスクトップを見つけるまで [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ツリーを上方向へ移動する例を次に示します。  そのすぐ下の要素は指定した要素の親ウィンドウです。  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## 使用例  
 次の例では、<xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> と <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> を使用して、コントロール ビュー内にある有効な [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]要素のサブツリー全体を表示する <xref:System.Windows.Forms.TreeView> を作成します。  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## 参照  
 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)