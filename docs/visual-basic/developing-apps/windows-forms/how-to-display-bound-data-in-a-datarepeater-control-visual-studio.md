---
title: "How to: Display Bound Data in a DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, data-binding"
  - "DataRepeater, displaying bound controls"
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Display Bound Data in a DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの最も一般的な用途は、データセットまたはその他のデータ ソースからバインドされたデータを表示することです。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールには、バインド コントロール以外に、静的ラベルやイメージなど項目ごとに繰り返し表示するコントロールも追加することが必要な場合があります。  詳細については、「[How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定し、データ ソースを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> プロパティに割り当てることで、実行時にデータ ソースにバインドすることもできます。  この場合、データ ソースとのすべてのやり取りを管理する必要があります。  詳細については、「[Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### データ バインド DataRepeater を作成するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  サイズ変更ハンドルをドラッグしてコントロールのサイズを設定し、移動ハンドルをドラッグしてコントロールの位置を指定します。  
  
     このコントロールには四角形の領域が 2 つあります。  上部領域は*項目テンプレート*であり、このテンプレートに追加したコントロールは <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール内の項目ごとに繰り返されます。  下部領域は*ビューポート*であり、ここに項目が表示されます。  
  
     \[プロパティ\] ウィンドウで **Size** プロパティおよび **Position** プロパティを変更することによって、コントロールまたは項目テンプレートのサイズおよび位置を変更することもできます。  
  
3.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
    > [!NOTE]
    >  **\[データ ソース\]** ウィンドウが空の場合は、そのウィンドウにデータ ソースを追加します。  詳細については、「[データ ソースの概要](/visual-studio/data-tools/add-new-data-sources)」を参照してください。  
  
4.  **\[データ ソース\]** ウィンドウで、バインドするデータが含まれるテーブルの最上位ノードを選択します。  
  
5.  テーブル ノードのドロップダウン リストの `Details` をクリックして、テーブルのドロップ タイプを `Details` に変更します。  
  
6.  テーブル ノードを選択し、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの項目テンプレート領域にドラッグします。  
  
     各フィールドに表示するコントロールの種類を指定できます。  詳細については、「[\[データ ソース\] ウィンドウからドラッグしたときに作成されるコントロールを設定する](/visual-studio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)