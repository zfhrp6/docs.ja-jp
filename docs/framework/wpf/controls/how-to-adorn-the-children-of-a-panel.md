---
title: "方法 : パネルの子を装飾する | Microsoft Docs"
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
  - "装飾, バインド (パネルの子に)"
  - "Panel コントロール, バインド (子に装飾を)"
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : パネルの子を装飾する
この例では、指定した <xref:System.Windows.Controls.Panel> の子にプログラムによって装飾をバインドする方法を示します。  
  
## 使用例  
 Adorner を <xref:System.Windows.Controls.Panel> の子にバインドするには、次の手順を実行します。  
  
1.  新しい <xref:System.Windows.Documents.AdornerLayer> オブジェクトを宣言し、`static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> メソッドを呼び出して、子が装飾の対象となる要素の装飾層を検出します。  
  
2.  親要素の子を列挙し、<xref:System.Windows.Documents.AdornerLayer.Add%2A> メソッドを呼び出して Adorner を各子要素にバインドします。  
  
 次の例では、SimpleCircleAdorner \(前述\) を <xref:System.Windows.Controls.StackPanel> の子 \(名前は *myStackPanel*\) にバインドしています。  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
>  Adorner を別の要素にバインドするために [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用することは、現在サポートされていません。  
  
## 参照  
 [装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)