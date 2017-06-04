---
title: "方法 : グリッドの子要素を配置する | Microsoft Docs"
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
  - "グリッド コントロール, 配置 (子要素を)"
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : グリッドの子要素を配置する
この例では、<xref:System.Windows.Controls.Grid> 上で定義された get メソッドおよび set メソッドを使用して子要素を配置する方法を示します。  
  
## 使用例  
 それぞれ 3 つの列と行を持つ親 <xref:System.Windows.Controls.Grid> 要素 \(`grid1`\) を定義する例を次に示します。  子 <xref:System.Windows.Shapes.Rectangle> 要素 \(`rect1`\) は、<xref:System.Windows.Controls.Grid> の列 0、行 0 の位置に追加されます。  <xref:System.Windows.Controls.Button> は、<xref:System.Windows.Controls.Grid> 内で <xref:System.Windows.Shapes.Rectangle> 要素の位置を変更するために呼び出すことができるメソッドを表します。  ボタンをクリックすると、関連メソッドがアクティブになります。  
  
 [!code-xml[gridGetSetMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml#1)]  
  
 次の分離コードの例では、ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントによって実行されるメソッドを処理します。  この例では、これらのメソッド呼び出しを <xref:System.Windows.Controls.TextBlock> 要素に書き出し、関連する get メソッドを使用して、新しいプロパティ値を文字列として出力します。  
  
 [!code-csharp[gridGetSetMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)