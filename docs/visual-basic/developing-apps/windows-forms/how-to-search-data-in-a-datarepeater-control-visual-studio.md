---
title: "How to: Search Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, implementing search"
  - "DataRepeater, searching data"
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Search Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

大量のレコードが含まれる <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを使用しているとき、ユーザーが特定のレコードを検索できるようにすることが必要になる場合があります。  コントロール自体でデータを検索するのではなく、基になる <xref:System.Windows.Forms.BindingSource> にクエリを実行することで検索を実装できます。  項目が見つかったら、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> プロパティを使用してその項目を選択し、スクロールして表示できます。  
  
### 検索を実装するには  
  
1.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを含んでいるフォームに、**ツールボックス**から <xref:System.Windows.Forms.TextBox> コントロールをドラッグします。  
  
2.  \[プロパティ\] ウィンドウで、**Name** プロパティを SearchTextBox に変更します。  
  
3.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを含んでいるフォームに、**ツールボックス**から <xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
4.  \[プロパティ\] ウィンドウで、**Name** プロパティを SearchButton に変更します。  **Text** プロパティを Search に変更します。  
  
5.  <xref:System.Windows.Forms.Button> コントロールをダブルクリックしてコード エディターを開き、`SearchButton_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-cs[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     *ProductsBindingSource* を <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> の <xref:System.Windows.Forms.BindingSource> の名前で置き換え、*ProductID* を検索するフィールドの名前で置き換えます。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)