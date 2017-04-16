---
title: "方法 : 複雑なグリッドを作成する | Microsoft Docs"
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
  - "カレンダー, 作成"
  - "グリッド コントロール, 作成, 複雑なグリッド"
  - "月別カレンダー, 作成"
ms.assetid: 4ce3040a-a156-4364-9596-98ca1eca5550
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 複雑なグリッドを作成する
この例では、<xref:System.Windows.Controls.Grid> を使用して月別カレンダーと同様のレイアウトを作成する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Controls.RowDefinition> クラスと <xref:System.Windows.Controls.ColumnDefinition> クラスを使用して、8 つの行と 8 つの列を定義します。  <xref:System.Windows.Controls.Grid.ColumnSpan%2A?displayProperty=fullName> 添付プロパティと <xref:System.Windows.Controls.Grid.RowSpan%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Shapes.Rectangle> 要素と共に使用し、さまざまな列と行の背景を塗りつぶします。  このようなデザインが可能なのは、<xref:System.Windows.Controls.Grid> 内の各セルに複数の要素が存在できるためです。これは、<xref:System.Windows.Controls.Grid> と <xref:System.Windows.Documents.Table> の本質的な違いです。  
  
 この例では、カレンダーの見た目を良くし、読みやすくするために、垂直グラデーションを使用して列と行を塗りつぶします \(<xref:System.Windows.Shapes.Shape.Fill%2A>\)。  スタイル設定された <xref:System.Windows.Controls.TextBlock> 要素は、日付と曜日を表します。  <xref:System.Windows.Controls.TextBlock> 要素は、<xref:System.Windows.FrameworkElement.Margin%2A> プロパティと、アプリケーションのスタイル内で定義された配置プロパティを使用して、それぞれのセル内の絶対位置に配置されます。  
  
 [!code-xml[GridComplex#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridComplex/CS/default.xaml#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.Documents.TableCell>   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)