---
title: "How to: Display Unbound Controls in a DataRepeater Control (Visual Studio) | Microsoft Docs"
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
  - "DataRepeater, adding unbound controls"
  - "DataRepeater"
  - "displaying unbound data"
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

バインド コントロール以外に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで項目ごとに繰り返される静的ラベルやイメージなどのコントロールも <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> に追加することが必要な場合があります。  
  
> [!NOTE]
>  また、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> にはバインド コントロールが少なくとも 1 つは必要であり、バインド コントロールがなければ実行時に何も表示されません。  
  
### DataRepeater に非バインド コントロールを追加するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  サイズ変更ハンドルをドラッグしてコントロールのサイズを設定し、移動ハンドルをドラッグしてコントロールの位置を指定します。  
  
     \[プロパティ\] ウィンドウで **Size** プロパティおよび **Position** プロパティを変更することによって、コントロールのサイズおよび位置を変更することもできます。  
  
3.  少なくとも 1 つのデータ バインド コントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに追加します。  詳細については、「[How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
4.  **ツールボックス**からコントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域にドラッグします。  
  
     このコントロールには四角形の領域が 2 つあります。  内部領域は*項目テンプレート*であり、このテンプレートに追加したコントロールは実行時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール内の項目ごとに繰り返されます。  外部領域は、*ビューポート*であり、この領域に項目が表示され、この領域に追加されたコントロールは実行時に表示されません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)