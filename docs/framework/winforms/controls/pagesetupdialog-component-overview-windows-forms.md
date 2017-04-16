---
title: "PageSetupDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "PageSetupDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "[ページ設定] ダイアログ ボックス, 表示"
  - "PageSetupDialog コンポーネント"
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# PageSetupDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.PageSetupDialog> コンポーネントは、Windows ベースのアプリケーションで印刷時のページ設定に使用する定義済みダイアログ ボックスです。  このコントロールは、独自のダイアログ ボックスを使用せずにページ設定を行うための簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。  罫線と余白の調整、ヘッダーとフッター、および印刷の縦向きまたは横向きを設定できます。  Windows の標準のダイアログ ボックスを使用して、一般的な基本機能を持つアプリケーションを作成できます。  
  
## 主要なプロパティおよびメソッド  
 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用して、実行時にダイアログを表示します。  このコンポーネントには、ページ単位で適用されるプロパティ \(<xref:System.Drawing.Printing.PrintDocument> クラス\) とすべてのドキュメントに適用されるプロパティ \(<xref:System.Drawing.Printing.PageSettings> クラス\) があります。  また、<xref:System.Windows.Forms.PageSetupDialog> コンポーネントを使用して、<xref:System.Drawing.Printing.PrinterSettings> クラスに格納される特定のプリンター設定を決定できます。  
  
 フォームに登録すると、<xref:System.Windows.Forms.PageSetupDialog> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.PageSetupDialog>   
 [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)