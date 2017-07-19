---
title: "方法 : 要素に装飾をバインドする | Microsoft Docs"
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
  - "装飾, バインド (指定した UIElement に)"
  - "UIElements, バインド (装飾を)"
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 要素に装飾をバインドする
この例では、指定した <xref:System.Windows.UIElement> にプログラムによって装飾をバインドする方法を示します。  
  
## 使用例  
 Adorner を特定の <xref:System.Windows.UIElement> にバインドするには、次の手順を実行します。  
  
1.  `static` メソッド <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> を呼び出し、修飾対象の <xref:System.Windows.UIElement> の <xref:System.Windows.Documents.AdornerLayer> オブジェクトを取得します。  <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> は、指定した **UIElement** を起点にしてビジュアル ツリーを上方向に検索し、最初に見つかった修飾層を返します。  \(Adorner のレイヤーが見つからない場合は、メソッドにより null が返されます。\)  
  
2.  <xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出し、対象の **UIElement** に装飾をバインドします。  
  
 次の例では、SimpleCircleAdorner \(前述\) を <xref:System.Windows.Controls.TextBox> \(名前は *myTextBox*\) にバインドしています。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Adorner を別の要素にバインドするために [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用することは、現在サポートされていません。  
  
## 参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)