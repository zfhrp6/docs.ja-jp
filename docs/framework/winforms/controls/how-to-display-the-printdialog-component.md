---
title: '方法 : PrintDialog コンポーネントを表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532188"
---
# <a name="how-to-display-the-printdialog-component"></a>方法 : PrintDialog コンポーネントを表示する
<xref:System.Windows.Forms.PrintDialog>コンポーネントは、多くのユーザーに習熟する標準の Windows 印刷 ダイアログ ボックス。 あるため、ユーザーはすぐに慣れる、使用すると役に立つなります、<xref:System.Windows.Forms.PrintDialog>コンポーネントです。  
  
### <a name="to-display-the-printdialog-component"></a>PrintDialog コンポーネントを表示するには  
  
-   呼び出す、<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッド アプリケーションのコード内からです。  
  
     コンポーネントが表示されると、ユーザーはそれを使用して印刷ジョブのプロパティを設定します。 これらに保存、 <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting`クラス (および<xref:System.Drawing.Printing.PageSettings>クラス、ユーザーがアクセスする場合、 [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)を通じて、<xref:System.Windows.Forms.PrintDialog>コンポーネント) その印刷ジョブに関連付けられています。 その後で、設定されたプロパティを呼び出して印刷ジョブの詳細を確認できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: 標準の Windows フォーム印刷ジョブを作成する](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [方法: 実行時に PrintDialog のユーザー入力をキャプチャする](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)
