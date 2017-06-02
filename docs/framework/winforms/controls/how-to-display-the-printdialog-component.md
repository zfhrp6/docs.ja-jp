---
title: "方法 : PrintDialog コンポーネントを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "[印刷] ダイアログ ボックス, 表示"
  - "PrintDialog コンポーネント [Windows フォーム], 表示"
  - "印刷 [Windows フォーム], 表示 (印刷ダイアログ ボックスを)"
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : PrintDialog コンポーネントを表示する
<xref:System.Windows.Forms.PrintDialog> コンポーネントは、多くのユーザーにお馴染みの Windows の標準印刷ダイアログ ボックスです。  ユーザーが簡単に使用できるため、<xref:System.Windows.Forms.PrintDialog> コンポーネントを使用することをお勧めします。  
  
### PrintDialog コンポーネントを表示するには  
  
-   アプリケーションのコードから <xref:System.Windows.Forms.Form.ShowDialog%2A> メソッドを呼び出します。  
  
     コンポーネントが表示されると、ユーザーはそれを使用して印刷ジョブのプロパティを設定します。  この設定は、印刷ジョブに関連付けられている [PrinterSettings](frlrfSystemDrawingPrintingPrinterSettingsMembersTopic) クラス \(ユーザーが <xref:System.Windows.Forms.PrintDialog> コンポーネントを通じて [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) にアクセスしている場合は [PageSettings](frlrfSystemDrawingPrintingPageSettingsMembersTopic) クラス\) に保存されます。  その後で、設定されたプロパティを呼び出して印刷ジョブの詳細を確認できます。  
  
## 参照  
 [方法 : 標準の Windows フォーム印刷ジョブを作成する](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)   
 [方法 : 実行時に PrintDialog のユーザー入力をキャプチャする](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)   
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)   
 [PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)