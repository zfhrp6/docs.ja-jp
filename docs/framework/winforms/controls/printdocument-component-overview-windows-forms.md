---
title: "PrintDocument コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "PrintDocument"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "PrintDocument コンポーネント [Windows フォーム], PrintDocument コンポーネントの概要"
  - "印刷 [Windows フォーム], PrintDocument コンポーネント"
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# PrintDocument コンポーネントの概要 (Windows フォーム)
Windows フォームの [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) コンポーネントは、Windows ベースのアプリケーション内でドキュメントの印刷を行うために、印刷対象と機能を定義するプロパティを設定するときに使用します。  このコンポーネントを [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) コンポーネントと一緒に使用すると、ドキュメント印刷のすべての設定を制御できます。  
  
## PrintDocument コンポーネントの操作  
 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用するのは主に次の 2 つの場合です。  
  
-   簡易印刷ジョブ \(特定のテキスト ファイルを印刷する場合など\)。  簡易印刷ジョブの場合は、<xref:System.Drawing.Printing.PrintDocument> コンポーネントを Windows フォームに追加してから、<xref:System.Drawing.Printing.PrintDocument.PrintPage> イベント ハンドラーにファイル印刷のプログラミング ロジックを登録します。  このプログラミング ロジックでは、最後に <xref:System.Drawing.Printing.PrintDocument.Print%2A> メソッドを使用してドキュメントを印刷するようにします。  このメソッドは、<xref:System.Drawing.Printing.PrintPageEventArgs> クラスの <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> プロパティに格納されている <xref:System.Drawing.Graphics> オブジェクトをプリンターに送信します。  <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使用してテキスト ドキュメントを印刷する方法を示す例については、「[方法 : Windows フォームで複数ページのテキスト ファイルを印刷する](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)」を参照してください。  
  
-   より複雑な印刷ジョブ \(作成した印刷ロジックを再利用する場合など\)。  作成した印刷ロジックを再利用する場合は、<xref:System.Drawing.Printing.PrintDocument> の派生コンポーネントを新規作成し、<xref:System.Drawing.Printing.PrintDocument.PrintPage> イベントをオーバーライドします。オーバーライドの詳細については、Visual Basic では [Overrides](../Topic/Overrides%20\(Visual%20Basic\).md)、C\# では [override](../Topic/override%20\(C%23%20Reference\).md) のトピックをそれぞれ参照してください。  
  
 フォームに登録すると、<xref:System.Drawing.Printing.PrintDocument> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Drawing.Graphics>   
 <xref:System.Drawing.Printing.PrintDocument>   
 [Windows フォームにおける印刷のサポート](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)   
 [PrintDocument コンポーネント](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)