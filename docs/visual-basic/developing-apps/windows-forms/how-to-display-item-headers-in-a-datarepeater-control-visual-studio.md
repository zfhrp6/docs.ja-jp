---
title: "How to: Display Item Headers in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, item headers"
  - "DataRepeater, selection indicators"
ms.assetid: 37321447-0ffa-43e1-bdc9-0480e392b90f
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# How to: Display Item Headers in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目ヘッダーは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> が選択されていることを示すビジュアル インジケーターです。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> \(既定値\) に設定されている場合、項目ヘッダーは各項目の左に表示されます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> に設定されている場合、項目ヘッダーは各項目の上に表示されます。  
  
 項目を初めて選択したとき、項目ヘッダーは <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> プロパティで指定されている色で表示され、白い矢印アイコンが表示されます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> を <xref:System.Drawing.Color.White%2A> に設定した場合は、項目を初めて選択したときに選択記号は表示されません。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> 内のフィールドがフォーカスを得ると、項目ヘッダーの色が <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> の背景色に変更され、矢印アイコンが黒に変わります。  データが変更されると、項目ヘッダーに鉛筆の記号が表示されます。  
  
 項目ヘッダーの既定の幅 \(<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> プロパティが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles> に設定されている場合は高さ\) は 15 ピクセルです。  この幅は、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティを設定して変更できます。  
  
> [!NOTE]
>  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティが 11 未満の値に設定されている場合、項目ヘッダー内のインジケーター記号は表示されません。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> プロパティを **False** に設定することによって、項目ヘッダーを非表示にできます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> を **False** に設定した場合、項目が選択されていることを示すものは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> の境界線を囲む点線のみです。  
  
> [!NOTE]
>  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベントで <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> プロパティを監視することによって、独自の選択インジケーターを設定することもできます。  詳細については、「<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>」を参照してください。  
  
### 項目ヘッダーの外観を変更するには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下部領域を選択します。  
  
    > [!NOTE]
    >  コントロールの下部領域を選択する必要があります。  項目テンプレート セクションを選択すると、\[プロパティ\] ウィンドウに異なるプロパティ一式が表示されます。  
  
2.  \[プロパティ\] ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> プロパティを使用して項目ヘッダーの色を変更します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> を <xref:System.Drawing.Color.White%2A> に設定した場合は、項目を初めて選択したときに選択記号は表示されません。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティを使用して、項目ヘッダーの幅 \(または高さ\) を変更します。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティが 11 未満の値に設定されている場合、項目ヘッダー内のインジケーター記号は表示されません。  
  
### 項目ヘッダーを非表示にするには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの下部領域を選択します。  
  
    > [!NOTE]
    >  コントロールの下部領域を選択する必要があります。  項目テンプレート セクションを選択すると、\[プロパティ\] ウィンドウに異なるプロパティ一式が表示されます。  
  
2.  \[プロパティ\] ウィンドウで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderVisible%2A> プロパティを **False** に設定します。  
  
     <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 内で項目が選択されていることを示すものは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> の境界線を囲む点線のみです。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)