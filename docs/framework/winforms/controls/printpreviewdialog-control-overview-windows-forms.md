---
title: "PrintPreviewDialog コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PrintPreviewDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintPreviewDialog コントロール (デザイナーを使用), PrintPreviewDialog の概要"
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# PrintPreviewDialog コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.PrintPreviewDialog> コントロールは、[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) を印刷時の状態で表示する、定義済みダイアログ ボックスです。  このコントロールは、独自のダイアログ ボックスを使用しない簡易ソリューションとして、Windows ベースのアプリケーションで使用します。  このコントロールには、印刷を開始するボタン、ズーム イン用のボタン、1 ページまたは複数ページを表示するボタン、およびダイアログ ボックスを閉じるためのボタンがあります。  
  
## 主要なプロパティおよびメソッド  
 このコントロールの主要なプロパティは、プレビューするドキュメントを設定する <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> プロパティです。  ドキュメントは、<xref:System.Drawing.Printing.PrintDocument> オブジェクトである必要があります。  ダイアログ ボックスを表示するには、コントロールの <xref:System.Windows.Forms.Form.ShowDialog%2A> メソッドを呼び出す必要があります。  アンチエイリアシングを使用すると、文字の外観は滑らかになりますが、表示は遅くなります。使用する場合は、<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> プロパティを `true` に設定します。  
  
 いくつかのプロパティは、<xref:System.Windows.Forms.PrintPreviewDialog> に含まれる <xref:System.Windows.Forms.PrintPreviewControl> を介して使用できます。  <xref:System.Windows.Forms.PrintPreviewControl> をフォームに追加する必要はありません。コントロールは、ダイアログをフォームに追加したときに自動的に <xref:System.Windows.Forms.PrintPreviewDialog> に含められます。<xref:System.Windows.Forms.PrintPreviewControl> を介して使用できるプロパティの例として、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> プロパティおよび <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> プロパティがあります。これらのプロパティは、コントロール上で横方向および縦方向に表示されるページの数を決定します。  <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> プロパティには、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] では `PrintPreviewDialog1.PrintPreviewControl.Columns`、[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] では `printPreviewDialog1.PrintPreviewControl.Columns`、または [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)] では `printPreviewDialog1->PrintPreviewControl->Columns` としてアクセスできます。  
  
## 参照  
 <xref:System.Windows.Forms.PrintPreviewDialog>   
 [PrintPreviewControl コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)   
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)