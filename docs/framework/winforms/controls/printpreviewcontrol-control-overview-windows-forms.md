---
title: "PrintPreviewControl コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PrintPreviewControl>表示に使用される、 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)印刷されたときに表示されます。 このコントロールには、ボタンやその他のユーザー インターフェイスの要素がないため、通常は、独自の印刷プレビューのユーザー インターフェイスを作成する場合にのみ <xref:System.Windows.Forms.PrintPreviewControl> を使用します。 標準のユーザー インターフェイスを実行する場合に、使用、<xref:System.Windows.Forms.PrintPreviewDialog>制御; を参照してください[PrintPreviewDialog コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)の概要について説明します。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールのキー プロパティは<xref:System.Windows.Forms.PrintPreviewControl.Document%2A>、プレビューするドキュメントを設定します。 ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。 印刷するドキュメントの作成の概要については、次を参照してください。 [PrintDocument コンポーネントの概要](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)と[Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)です。 <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティがコントロールの水平方向および垂直方向に表示されているページの数を決定します。 アンチ エイリアスが滑らかにテキストを行うことができます。 が、低速です。 表示することもできます。これを使用する設定、<xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A>プロパティを`true`です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [PrintPreviewDialog コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [PrintPreviewControl コントロール](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
