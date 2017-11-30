---
title: "PrintPreviewDialog コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3c898dc24c9a4418e3af45fce507e6befcf905a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは、構成済みのダイアログ ボックスを表示するために使用する方法、 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)印刷したときに表示されます。 独自のダイアログ ボックスではなく簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。 このコントロールには、印刷を開始するボタン、ズーム イン用のボタン、1 ページまたは複数ページを表示するボタン、およびダイアログ ボックスを閉じるためのボタンが含まれています。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 コントロールのキー プロパティは<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>、プレビューするドキュメントを設定します。 ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。 ダイアログ ボックスを表示するために呼び出す必要があります、<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッドです。 アンチ エイリアスが滑らかにテキストを行うことができます。 が、低速です。 表示することもできます。これを使用する設定、<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>プロパティを`true`です。  
  
 特定のプロパティは、<xref:System.Windows.Forms.PrintPreviewControl>を<xref:System.Windows.Forms.PrintPreviewDialog>が含まれています。 (これを追加する必要はありません<xref:System.Windows.Forms.PrintPreviewControl>フォームに含まれている自動的に、<xref:System.Windows.Forms.PrintPreviewDialog>をフォームにダイアログ ボックスを追加するとします)。を通じて使用可能なプロパティの例については、<xref:System.Windows.Forms.PrintPreviewControl>は、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティで、コントロールの水平方向および垂直方向に表示されているページの数を決定します。 アクセスすることができます、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>プロパティとして`PrintPreviewDialog1.PrintPreviewControl.Columns`で[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、`printPreviewDialog1.PrintPreviewControl.Columns`で[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、または`printPreviewDialog1->PrintPreviewControl->Columns`で[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [PrintPreviewControl コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
