---
title: "方法 : ListView のカスタム表示モードを作成する | Microsoft Docs"
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
  - "ListView コントロール, 作成 (カスタム表示モードを)"
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : ListView のカスタム表示モードを作成する
この例では、<xref:System.Windows.Controls.ListView> コントロールのカスタム <xref:System.Windows.Controls.ListView.View%2A> モードを作成する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.ListView> コントロールのカスタム ビューを作成する場合は、<xref:System.Windows.Controls.ViewBase> クラスを使用する必要があります。  <xref:System.Windows.Controls.ViewBase> クラスから派生した、`PlainView` と呼ばれる表示モードを次の例に示します。  
  
 [!code-csharp[ListViewCustomView#PlainView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 カスタム ビューにスタイルを適用するには、<xref:System.Windows.Style> クラスを使用します。  `PlainView` 表示モードの <xref:System.Windows.Style> を定義する例を次に示します。  前の例では、このスタイルは、`PlainView` に対して定義されている <xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A> プロパティの値として設定されています。  
  
 [!code-xml[ListViewCustomView#PlainViewStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 カスタム表示モードでのデータのレイアウトを定義するには、<xref:System.Windows.DataTemplate> オブジェクトを定義します。  `PlainView` 表示モードでのデータの表示に使用できる <xref:System.Windows.DataTemplate> を定義する例を次に示します。  
  
 [!code-xml[ListViewCustomView#PlainViewDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 前の例で定義した <xref:System.Windows.DataTemplate> を使用する `PlainView` 表示モードの <xref:System.Windows.ResourceKey> を定義する方法を次の例に示します。  
  
 [!code-xml[ListViewCustomView#PlainViewtileView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 <xref:System.Windows.Controls.ListView> コントロールでは、<xref:System.Windows.Controls.ListView.View%2A> プロパティをリソース キーに設定することで、カスタム ビューを使用できるようになります。  `PlainView` を <xref:System.Windows.Controls.ListView> の表示モードとして指定する方法を次の例に示します。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 サンプル全体については、[複数のビューを持つ ListView のサンプル](http://go.microsoft.com/fwlink/?LinkID=160013)を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)