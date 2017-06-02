---
title: "Invoke a Control Using UI Automation | Microsoft Docs"
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
  - "invoking controls"
  - "UI Automation, invoking controls"
  - "controls, invoking"
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
caps.latest.revision: 15
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 15
---
# Invoke a Control Using UI Automation
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の最新情報については、「[Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」をご覧ください。  
  
 このトピックでは、次のタスクを実行する方法について示します。  
  
-   ターゲット アプリケーションの [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューを調べて、特定のプロパティ条件に一致するコントロールを検索する。  
  
-   各コントロールに対して <xref:System.Windows.Automation.AutomationElement> を作成する。  
  
-   <xref:System.Windows.Automation.InvokePattern> コントロール パターンをサポートする [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要素から <xref:System.Windows.Automation.InvokePattern> オブジェクトを取得する。  
  
-   <xref:System.Windows.Automation.InvokePattern.Invoke%2A> を使用して、クライアントのイベント ハンドラーからコントロールを呼び出す。  
  
## 使用例  
 この例では、<xref:System.Windows.Automation.AutomationElement> クラスの <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> メソッドを使用して <xref:System.Windows.Automation.InvokePattern> オブジェクトを生成し、<xref:System.Windows.Automation.InvokePattern.Invoke%2A> メソッドを使用してコントロールを呼び出します。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## 参照  
 [InvokePattern and ExpandCollapsePattern Menu Item Sample](http://msdn.microsoft.com/ja-jp/b7fa141c-e2d1-4da2-a27f-81a7d1172210)