---
title: "Windows フォームにおける印刷のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "フォーム, 印刷 (デザイナーを使用して)"
  - "印刷 [Windows フォーム]"
  - "印刷 [Windows フォーム], 印刷のサポート"
  - "印刷, Windows フォーム, サポート"
  - "Windows フォーム, 印刷"
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォームにおける印刷のサポート
Windows フォームにおける印刷では主に、ユーザーによる印刷を可能にするための [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) コンポーネントと、Windows オペレーティング システムを常用しているユーザーに見慣れたグラフィカル インターフェイスを提供するための [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)、[PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)、および [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) が使用されます。  
  
 通常、印刷を行う場合には、<xref:System.Drawing.Printing.PrintDocument> コンポーネントの新しいインスタンスを作成し、<xref:System.Drawing.Printing.PrinterSettings> クラスおよび <xref:System.Drawing.Printing.PageSettings> クラスを使用して印刷対象を定義してから、<xref:System.Drawing.Printing.PrintDocument.Print%2A> メソッドを呼び出してドキュメントを実際に印刷します。  
  
 Windows ベースのアプリケーションから印刷を行っている間、<xref:System.Drawing.Printing.PrintDocument> コンポーネントは、印刷中止ダイアログ ボックスを表示して、印刷が実行中であることをユーザーに通知し、ユーザーが印刷ジョブをキャンセルできるようにします。  
  
## このセクションの内容  
 [方法 : 標準の Windows フォーム印刷ジョブを作成する](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用して Windows フォームで印刷を行う方法について説明します。  
  
 [方法 : 実行時に PrintDialog のユーザー入力をキャプチャする](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 選択した印刷オプションを <xref:System.Windows.Forms.PrintDialog> コンポーネントを使用してプログラムで変更する方法について説明します。  
  
 [方法 : Windows フォームでユーザーのコンピューターに接続されたプリンターを選択する](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 実行時に <xref:System.Windows.Forms.PrintDialog> コンポーネントを使用してプリンターを変更する方法について説明します。  
  
 [方法 : Windows フォームでグラフィックスを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 プリンターにグラフィックを送る方法について説明します。  
  
 [方法 : Windows フォームで複数ページのテキスト ファイルを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 プリンターにテキストを送る方法について説明します。  
  
 [方法 : Windows フォームの印刷ジョブを完了する](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 ユーザーに印刷ジョブの完了を通知する方法について説明します。  
  
 [方法 : Windows フォームを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 現在のフォームのコピーを印刷する方法について説明します。  
  
 [方法 : Windows フォームで印刷プレビューを使用して印刷する](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 文書を印刷するために <xref:System.Windows.Forms.PrintPreviewDialog> を使用する方法について説明します。  
  
## 関連項目  
 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用する方法について説明します。  
  
 [PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <xref:System.Windows.Forms.PrintDialog> コンポーネントを使用する方法について説明します。  
  
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <xref:System.Windows.Forms.PrintPreviewDialog> コントロールを使用する方法について説明します。  
  
 [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <xref:System.Windows.Forms.PageSetupDialog> コンポーネントを使用する方法について説明します。  
  
 <xref:System.Drawing.Printing>  
 <xref:System.Drawing.Printing> 名前空間に含まれるクラスについて説明します。