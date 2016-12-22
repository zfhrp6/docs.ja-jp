---
title: "How to: Change the Layout of a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, changing layout style"
  - "DataRepeater, changing orientation"
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Change the Layout of a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは、垂直方向 \(項目を縦にスクロールする\) または水平方向 \(項目を横にスクロールする\) に表示できます。  この方向は、デザイン時にも実行時にも、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティを変更することによって変更できます。  実行時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティを変更する場合は、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> のサイズと子コントロールの位置も変更することが必要になる場合があります。  
  
> [!NOTE]
>  実行時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 上のコントロールの位置を変更する場合、コントロールの位置を変更するコード ブロックの先頭と末尾で、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> メソッドおよび <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> メソッドを呼び出す必要があります。  
  
### デザイン時にレイアウトを変更するには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを選択します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの上部にある <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> 領域ではなく、下部の領域でコントロールの外枠をクリックして選択する必要があります。  
  
2.  \[プロパティ\] ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> または <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> に設定します。  
  
### 実行時にレイアウトを変更するには  
  
1.  ボタンまたはメニューの `Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  多くの場合、例のセクションに示されているようなコードを追加して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> のサイズおよびコントロールの位置を新しい方向に合わせて変更する必要があります。  
  
## 使用例  
 イベント ハンドラー内で <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> イベントに応答する方法を次の例に示します。  この例では、フォームに `DataRepeater1` という名前の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールが配置され、そのコントロールの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> に `TextBox1` および `TextBox2` という名前の 2 つの <xref:System.Windows.Forms.TextBox> コントロールが配置されている必要があります。  
  
 [!code-cs[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)