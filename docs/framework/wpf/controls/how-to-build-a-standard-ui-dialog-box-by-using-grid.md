---
title: "方法 : グリッドを使用して標準 UI ダイアログ ボックスをビルドする | Microsoft Docs"
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
  - "ダイアログ ボックス, 作成"
  - "グリッド コントロール, 作成, ダイアログ ボックス"
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : グリッドを使用して標準 UI ダイアログ ボックスをビルドする
この例では、<xref:System.Windows.Controls.Grid> 要素を使用して、標準の[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ダイアログ ボックスを作成する方法を示します。  
  
## 使用例  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] オペレーティング システムの **\[ファイル名を指定して実行\]** ダイアログ ボックスに似たダイアログ ボックスを作成する例を次に示します。  
  
 この例では、<xref:System.Windows.Controls.Grid> を作成し、<xref:System.Windows.Controls.ColumnDefinition> クラスおよび <xref:System.Windows.Controls.RowDefinition> クラスを使用して、5 つの列と 4 つの行を定義しています。  
  
 次に、ダイアログ ボックスに表示するイメージを表すために、`RunIcon.png` という <xref:System.Windows.Controls.Image> を追加して配置します。  このイメージは、<xref:System.Windows.Controls.Grid> の第 1 列、第 1 行 \(左上隅\) に配置します。  
  
 次に、<xref:System.Windows.Controls.TextBlock> 要素を第 1 列に追加します。これは、第 1 行の最後の列までまたがります。  さらに、別の <xref:System.Windows.Controls.TextBlock> 要素を第 1 列、第 2 行に追加します。これは \[Open\] ボックスを表します。  その後に、もう一つ <xref:System.Windows.Controls.TextBlock> を追加します。これはデータ入力領域を表します。  
  
 最後に、**OK**、**Cancel**、および **Browse** の各イベントを表す 3 つの <xref:System.Windows.Controls.Button> 要素を最終行に追加します。  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 <xref:System.Windows.GridUnitType>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)