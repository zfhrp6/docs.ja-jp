---
title: "方法 : ポップアップのカスタム位置を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Popup コントロール, 指定 (カスタム位置を)"
ms.assetid: 28c24f39-d3aa-4ee2-b950-384b4a5dab92
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ポップアップのカスタム位置を指定する
<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> プロパティが <xref:System.Windows.Controls.Primitives.PlacementMode> に設定されている場合に、<xref:System.Windows.Controls.Primitives.Popup> コントロールのカスタム位置を指定する方法を次の例に示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> プロパティが <xref:System.Windows.Controls.Primitives.PlacementMode> に設定されると、<xref:System.Windows.Controls.Primitives.Popup> は <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> デリゲートの定義済みインスタンスを呼び出します。  このデリゲートは、ターゲット領域の左上隅および <xref:System.Windows.Controls.Primitives.Popup> の左上隅を基準として、表示先になり得る一連の相対位置を返します。  <xref:System.Windows.Controls.Primitives.Popup> は、最も見やすい位置に配置されます。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> プロパティを <xref:System.Windows.Controls.Primitives.PlacementMode> に設定することによって <xref:System.Windows.Controls.Primitives.Popup> の位置を定義する方法を次の例に示します。  この例では、<xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> デリゲートを作成して割り当てることによって <xref:System.Windows.Controls.Primitives.Popup> を配置する方法も示します。  コールバック デリゲートは、2 つの <xref:System.Windows.Controls.Primitives.CustomPopupPlacement> オブジェクトを返します。  最初の位置では <xref:System.Windows.Controls.Primitives.Popup> が画面の端に隠れる場合、<xref:System.Windows.Controls.Primitives.Popup> は 2 番目の位置に配置されます。  
  
 [!code-xml[PopupCustomPlacement#CustomPlacement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml#customplacement)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegateinstance)]
 [!code-vb[PopupCustomPlacement#DelegateInstance](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegateinstance)]  
  
 [!code-csharp[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupCustomPlacement/CSharp/Window1.xaml.cs#delegatedefinition)]
 [!code-vb[PopupCustomPlacement#DelegateDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PopupCustomPlacement/visualbasic/window1.xaml.vb#delegatedefinition)]  
  
 サンプル全体については、[ポップアップ配置のサンプル](http://go.microsoft.com/fwlink/?LinkID=160032)を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.Primitives.Popup>   
 [ポップアップの概要](../../../../docs/framework/wpf/controls/popup-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)