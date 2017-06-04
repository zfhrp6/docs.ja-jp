---
title: "PrintDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "PrintDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "[印刷] ダイアログ ボックス, 表示"
  - "PrintDialog コンポーネント [Windows フォーム], PrintDialog コンポーネントの概要"
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# PrintDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) コンポーネントは、Windows ベースのアプリケーションで出力先プリンターや印刷範囲などの印刷設定に使用する、定義済みダイアログ ボックスです。  このダイアログ ボックスは、独自のダイアログ ボックスを使用せずにプリンターなどの印刷設定を行うための簡易ソリューションとして使用します。  ドキュメント全体、選択したページ範囲、選択した部分など、さまざまな印刷範囲を指定できます。  Windows の標準のダイアログ ボックスを使用して、一般的な基本機能を持つアプリケーションを作成できます。  <xref:System.Windows.Forms.PrintDialog> コンポーネントは、<xref:System.Windows.Forms.CommonDialog> クラスを継承します。  
  
## コンポーネントの操作  
 実行時にダイアログ ボックスを表示するには、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用します。  このコンポーネントには、印刷ジョブ単位で適用されるプロパティ \(<xref:System.Drawing.Printing.PrintDocument> クラス\) とプリンター単位で適用されるプロパティ \(<xref:System.Drawing.Printing.PrinterSettings> クラス\) があります。  このいずれかを複数のプリンターで共有できます。  
  
 フォームに登録すると、<xref:System.Windows.Forms.PrintDialog> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.PrintDialog>   
 [PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)