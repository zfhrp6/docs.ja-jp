---
title: "方法 : GridSplitter を表示されるようにする | Microsoft Docs"
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
  - "GridSplitter コントロール, 確保 (可視性を)"
ms.assetid: 0a62a964-89c8-48f0-9023-5df721a8cf47
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : GridSplitter を表示されるようにする
この例では、<xref:System.Windows.Controls.GridSplitter> コントロールが <xref:System.Windows.Controls.Grid> 内で他のコントロールによって隠されないようにする方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Grid> コントロールの <xref:System.Windows.Controls.Panel.Children%2A> は、マークアップやコードに定義されている順序で描画されます。  <xref:System.Windows.Controls.GridSplitter> コントロールは、<xref:System.Windows.Controls.Panel.Children%2A> コレクションで最後の要素として定義されていない場合、または <xref:System.Windows.Controls.Panel.ZIndexProperty> の値が他のコントロールより低い場合に、他のコントロールによって隠される可能性があります。  
  
 <xref:System.Windows.Controls.GridSplitter> コントロールが隠されないようにするには、次のいずれかの操作を行います。  
  
-   <xref:System.Windows.Controls.GridSplitter> コントロールを、<xref:System.Windows.Controls.Grid> に最後の <xref:System.Windows.Controls.Panel.Children%2A> として追加します。  次の例では、<xref:System.Windows.Controls.GridSplitter> が <xref:System.Windows.Controls.Grid> の <xref:System.Windows.Controls.Panel.Children%2A> コレクションの最後の要素として示されています。  
  
 [!code-xml[GridSplitterSnips#GridSplitterLastChild](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterlastchild)]  
  
-   <xref:System.Windows.Controls.GridSplitter> の <xref:System.Windows.Controls.Panel.ZIndexProperty> に、このコントロールを隠す可能性のある他のコントロールより高い値を設定します。  次の例では、<xref:System.Windows.Controls.GridSplitter> コントロールの <xref:System.Windows.Controls.Panel.ZIndexProperty> に <xref:System.Windows.Controls.Button> コントロールより高い値を設定しています。  
  
 [!code-xml[GridSplitterSnips#GridSplitterZIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplitterzindex)]  
  
-   <xref:System.Windows.Controls.GridSplitter> を隠す可能性のあるコントロールにマージンを設定し、<xref:System.Windows.Controls.GridSplitter> が確実に表示されるようにします。  次の例では、<xref:System.Windows.Controls.GridSplitter> に重なって隠す可能性のあるコントロールにマージンを設定しています。  
  
 [!code-xml[GridSplitterSnips#GridSplitterMargin](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterSnips/CSharp/Window1.xaml#gridsplittermargin)]  
  
## 参照  
 <xref:System.Windows.Controls.GridSplitter>   
 [方法のトピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)