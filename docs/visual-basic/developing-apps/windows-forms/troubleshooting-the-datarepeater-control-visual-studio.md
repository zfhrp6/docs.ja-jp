---
title: "Troubleshooting the DataRepeater Control (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, troubleshooting"
ms.assetid: c0ab9469-eced-4f52-aa18-4bd8dd4f1a9a
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Troubleshooting the DataRepeater Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを使用するときに発生する可能性のある一般的な問題について説明します。  
  
## DataRepeater のキーボード イベントおよびマウス イベントが発生しない  
 キーボード イベントやマウス イベントなどの一部の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール イベントは発生しません。  これは仕様に基づく制限事項です。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール自体は <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> オブジェクトのコンテナーであるため、実行時にはアクセスできません。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> は、デザイン時にイベントを公開しません。  したがって、項目をクリックしても、項目にフォーカスがあるときにキーを押しても、イベントは発生しません。  
  
 ただし、<xref:System.Windows.Forms.Control.Padding%2A> プロパティが大きい値に設定されているために <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの端が隠されていない場合は例外です。  この場合、隠されていない余白部分をクリックするとイベントが発生します。  
  
 この問題を解決するには、<xref:System.Windows.Forms.Panel> コントロールを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> セクションに追加し、それ以外のコントロールをすべて <xref:System.Windows.Forms.Panel> に追加します。  次に、<xref:System.Windows.Forms.Panel> コントロールのキーボード イベントおよびマウス イベントのイベント ハンドラーにコードを追加します。  
  
## DataRepeater が部分的にバインド ナビゲーターの後ろに隠れる  
 フォームに先に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを追加し、次に **\[データ ソース\]** ウィンドウからデータ バインド コントロールを追加した場合、<xref:System.Windows.Forms.BindingNavigator> コントロールが <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの上に重なって表示される場合があります。  これは **\[データ ソース\]** ウィンドウの既知の制限事項であり、<xref:System.Windows.Forms.DataGridView> などの他のコントロールの場合と同じ動作です。  
  
 この問題を解決するには、デザイン時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールを <xref:System.Windows.Forms.BindingNavigator> コントロールより下へ移動するか、`Load` イベント ハンドラーに次のようなコードを追加します。  
  
```vb#  
DataRepeater1.Top = ProductsBindingNavigator.Height  
```  
  
```c#  
dataRepeater1.Top = productsBindingNavigator.Height;  
```  
  
## 実行時にコントロールが正しく表示されない  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロール内の一部のコントロールが、実行時に意図したとおりに表示されない場合があります。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> から <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> にコントロールを複製する処理では、必ずしもすべてのコントロールのすべてのプロパティが特定されるわけではありません。  たとえば、デザイン時に <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールに非バインド <xref:System.Windows.Forms.ListBox> コントロールを追加し、その <xref:System.Windows.Forms.ListBox.Items%2A> コレクションを文字列リストで設定した場合、<xref:System.Windows.Forms.ListBox> は実行時には空になります。  これは、<xref:System.Windows.Forms.ListBox.Items%2A> プロパティが複製処理の対象とならないからです。  
  
 この問題は、複製されないプロパティを <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> イベントで復元するなどの方法で解決できます。このイベントは既定の複製処理が完了した後に発生します。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemCloned> イベント ハンドラーで、<xref:System.Windows.Forms.ListBox> コントロールの <xref:System.Windows.Forms.ListBox.Items%2A> コレクションを修復する方法を次の例に示します。  
  
 [!code-cs[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/troubleshooting-the-datarepeater-control-visual-studio_1.cs)]
 [!code-vb[VbPowerPacksDataRepeaterItemCloned#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/troubleshooting-the-datarepeater-control-visual-studio_1.vb)]  
  
## 項目ヘッダーに選択記号が表示されない  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールで項目ヘッダーの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> プロパティを変更すると、選択した色によっては選択記号が見えなくなることがあります。  <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティを変更することによっても選択記号が見えなくなることがあります。  
  
 選択記号の色とサイズは変更できません。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> を <xref:System.Drawing.Color.White%2A> に設定すると、項目が初めて選択されたときに選択記号は見えません。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.SelectionColor%2A> を <xref:System.Drawing.Color.Black%2A> に設定すると、コントロールが選択されているときは選択記号が見えず、コントロールが編集モードのときは鉛筆の記号が見えません。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemHeaderSize%2A> プロパティが 11 未満の値に設定されている場合、項目ヘッダー内のインジケーター記号は表示されません。  
  
 独自の項目ヘッダーと選択記号を設定するには、<xref:System.Windows.Forms.PictureBox> コントロールを使用し、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールの <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> イベントで <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A> プロパティを監視します。  詳細については、「<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem.IsCurrent%2A>」を参照してください。  
  
## 参照  
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Layout of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)   
 [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)   
 [How to: Display Item Headers in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)   
 [How to: Disable Adding and Deleting DataRepeater Items](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)   
 [How to: Search Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)   
 [How to: Create a Master\/Detail Form by Using Two DataRepeater Controls](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)