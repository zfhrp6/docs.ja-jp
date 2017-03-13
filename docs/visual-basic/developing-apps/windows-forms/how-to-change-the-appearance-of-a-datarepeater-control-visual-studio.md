---
title: "How to: Change the Appearance of a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, customizing"
  - "DataRepeater, changing run time appearance"
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Change the Appearance of a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの外観は、デザイン時にプロパティを設定するか、実行時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベントを処理することで変更できます。  
  
 デザイン時にコントロールの項目テンプレート セクションを選択した状態で設定するプロパティは、実行時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> ごとに繰り返されます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール自体の外観に関連するプロパティは、実行時にコンテナーの一部が隠されていない状態の場合 \(<xref:System.Windows.Forms.Control.Padding%2A> プロパティが大きい値に設定されている場合など\) に限り、表示されます。  
  
 外観に関連するプロパティは、実行時に、条件に基づいて設定できます。  たとえば、スケジュール管理用のアプリケーションでは、項目の背景色を変更して、期限切れの項目を警告できます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラー内で、`If…Then` などの条件付きステートメントでプロパティを設定する場合は、`Else` 句も使用して、条件が満たされない場合の外観を指定する必要があります。  
  
### デザイン時に外観を変更するには  
  
1.  Windows フォーム デザイナーで、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート \(上部\) 領域を選択します。  
  
2.  \[プロパティ\] ウィンドウで、プロパティを選択して値を変更します。  外観に関連する一般的なプロパティとしては、<xref:System.Windows.Forms.Control.BackColor%2A>、<xref:System.Windows.Forms.Control.BackgroundImage%2A>、<xref:System.Windows.Forms.Panel.BorderStyle%2A>、<xref:System.Windows.Forms.Control.ForeColor%2A> などがあります。  
  
### 実行時に外観を変更するには  
  
1.  コード エディターで、\[イベント\] ボックスの一覧の **\[DrawItem\]** をクリックします。  
  
2.  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント ハンドラーに、プロパティを設定するコードを追加します。  
  
     [!code-cs[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## 使用例  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの一般的なカスタマイズの例として、行の色を交互にする、条件に基づいてフィールドの色を変更する、などが挙げられます。  このようなカスタマイズを行う方法を次の例に示します。  この例では、Northwind データベースの Products テーブルにバインドされた <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールがあることを前提としています。  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-cs[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 どちらのカスタマイズを行うときも、条件の一致不一致両方の場合について、プロパティを設定するコードを記述する必要があります。  `Else` 条件を指定しないと、実行時に予期しない結果が発生します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)