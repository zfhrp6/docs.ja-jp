---
title: "PrintPreviewControl コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "PrintPreviewControl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "印刷プレビュー"
  - "PrintPreviewControl コントロール"
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# PrintPreviewControl コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.PrintPreviewControl> は、[PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) を印刷時の状態で表示するために使用します。  <xref:System.Windows.Forms.PrintPreviewControl> にはボタンなどのユーザー インターフェイス要素がないため、通常は、独自の印刷プレビュー用ユーザー インターフェイスを作成する場合にだけ使用します。  標準のユーザー インターフェイスが必要な場合は、<xref:System.Windows.Forms.PrintPreviewDialog> コントロールを使用します。概要については「[PrintPreviewDialog コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)」を参照してください。  
  
## 主要なプロパティ  
 このコントロールの主要なプロパティは、プレビューするドキュメントを設定する <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> プロパティです。  ドキュメントは、<xref:System.Drawing.Printing.PrintDocument> オブジェクトである必要があります。  印刷用ドキュメントの作成の概要については、「[PrintDocument コンポーネントの概要](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)」と「[Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)」を参照してください。  <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> プロパティと <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> プロパティは、コントロール上で横方向および縦方向に表示されるページの数を決定します。  アンチエイリアシングを使用すると、文字の外観は滑らかになりますが、表示は遅くなります。使用する場合は、<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> プロパティを `true` に設定します。  
  
## 参照  
 <xref:System.Windows.Forms.PrintPreviewControl>   
 [PrintPreviewDialog コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)   
 [PrintPreviewControl コントロール](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)   
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)