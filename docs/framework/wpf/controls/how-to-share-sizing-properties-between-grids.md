---
title: "方法 : グリッド間でサイズ設定プロパティを共有する | Microsoft Docs"
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
  - "グリッド コントロール, 共有 (列のサイズ設定データを)"
  - "グリッド コントロール, 共有 (行のサイズ設定データを)"
  - "サイズ設定データ (グリッド コントロールの)"
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : グリッド間でサイズ設定プロパティを共有する
この例では、一貫したサイズ設定を行うために、<xref:System.Windows.Controls.Grid> の要素間で列と行のサイズ設定データを共有する方法を示します。  
  
## 使用例  
 次の例では、親 <xref:System.Windows.Controls.DockPanel> の子要素として 2 つの <xref:System.Windows.Controls.Grid> 要素を導入しています。  <xref:System.Windows.Controls.Grid> の <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> [添付プロパティ](GTMT)は、親 <xref:System.Windows.Controls.DockPanel> で定義されています。  
  
 この例では、2 つの <xref:System.Windows.Controls.Button> 要素を使用してプロパティの値を操作します。各要素は、Boolean プロパティ値の 1 つを表します。  <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A> プロパティ値が `true` に設定されている場合、<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> の各列または行メンバーは、行または列のコンテンツに関係なく、サイズ設定情報を共有します。  
  
 [!code-xml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 次の分離コード例では、ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントによって起動されるメソッドを処理します。  この例では、これらのメソッドの <xref:System.Windows.Controls.TextBlock> 要素に対する呼び出しの結果を記述しています。この要素は、関連する get メソッドを使用して新しいプロパティの値を文字列として出力します。  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)