---
title: "Introduction to the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "repeating data"
  - "DataRepeater, overview"
  - "DataRepeater"
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Introduction to the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic Power Packs の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは、データベース テーブルの行などの繰り返されるデータを表示するコントロールの、スクロール可能なコンテナーです。  データのレイアウトを詳細に制御する必要がある場合は、<xref:System.Windows.Forms.DataGridView> コントロールの代わりにこのコントロールを使用できます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> は、スクロール可能なビュー内に複数のインスタンスを作成することによって、関連するコントロールのグループを "繰り返し" ます。  これによって、ユーザーは複数のレコードを同時に表示できます。  
  
## 概要  
 デザイン時には、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは 2 つのセクションで構成されます。  外部セクションは*ビューポート*であり、このセクションに実行時にスクロール可能なデータが表示されます。  内部 \(上部\) セクションは*項目テンプレート*であり、このセクションに実行時に繰り返されるコントロールを配置します \(通常はデータ ソースのフィールドごとに 1 つのコントロールを配置\)。  項目テンプレート内のプロパティおよびコントロールは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> プロパティ内にカプセル化されます。  
  
 実行時には、各レコードがスクロールされて表示されると、データの表示に使用される仮想 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> オブジェクトに <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> がコピーされます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベントで、フィールドの値に基づいてフィールドを強調表示するなど、個別のレコードの表示をカスタマイズできます。  詳細については、「[How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの最も一般的な用途は、データベース テーブルまたはその他のバインド データ ソースからデータを表示することです。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは、[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado-md.md)] データ オブジェクト以外に、<xref:System.Collections.IList> インターフェイスを実装しているクラス \(配列も含まれます\)、<xref:System.ComponentModel.IListSource> インターフェイスを実装しているクラス、<xref:System.ComponentModel.IBindingList> インターフェイスを実装しているクラス、または <xref:System.ComponentModel.IBindingListView> インターフェイスを実装しているクラスにもバインドできます。  
  
### データ バインディング  
 一般に、データ バインディングは、**\[データ ソース\]** ウィンドウから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールにフィールドをドラッグして行います。  詳細については、「[How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
 大量のデータを処理する場合は、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> プロパティを `True` に設定して、使用可能なデータのサブセットを表示できます。  仮想モードでは、データ キャッシュを実装してそこから <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> にデータを読み込むことが必要であり、実行時にそのデータ キャッシュとのやり取りを制御する必要があります。  詳細については、「[Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールには、非バインド コントロールも表示できます。  たとえば、項目ごとに繰り返されるイメージを表示できます。  詳細については、「[How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
### イベント  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの最も重要なイベントは、新しい項目をスクロールして表示すると発生する <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベント、および、項目を選択すると発生する <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> イベントです。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベントを使用して、項目の外観を変更できます。  たとえば、負の値を強調表示できます。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> イベントを使用すると、項目が選択されたときにコントロールの値にアクセスできます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは、コード エディターにすべての標準コントロール イベントを公開します。  ただし、一部のイベントは使用しないでください。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール自体はフォーカスを取得しないので、実行時に `KeyDown`、`Click`、`MouseDown` などのキーボード イベントおよびマウス イベントが発生することはありません。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> は実行時にのみ作成されるので、デザイン時にイベントを公開しません。  キーボード イベントおよびマウス イベントを処理する必要がある場合は、デザイン時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> に <xref:System.Windows.Forms.Panel> コントロールを追加し、<xref:System.Windows.Forms.Panel> のイベントを処理できます。  詳細については、「[Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)」を参照してください。  
  
### カスタマイズ  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの外観と動作は、実行時にもデザイン時にも、多くの方法でカスタマイズできます。  プロパティを設定することによって、色の変更、項目ヘッダーの非表示化や変更、垂直方向から水平方向への変更など、さまざまな変更を行うことができます。  詳細については、「[How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)」、「[How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)」、および「[How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール自体に適用されるプロパティと、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> のみに適用されるプロパティがあることに注意してください。  プロパティを設定する前に、コントロールの正しいセクションを選択していることを確認してください。  詳細については、「[How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)」を参照してください。  
  
 その他のカスタマイズとして、レコードの追加または削除の権限の制御、検索機能の追加、関連データのマスター\/詳細形式の表示などがあります。  詳細については、「[How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)」、「[How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)」、および「[How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)」を参照してください。  
  
## 参照  
 [DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [チュートリアル: DataRepeater コントロールでのデータの表示](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)