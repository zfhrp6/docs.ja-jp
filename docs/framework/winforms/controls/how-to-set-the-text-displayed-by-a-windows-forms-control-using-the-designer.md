---
title: "方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 設定 (キャプションを)"
  - "Windows フォーム, 設定 (表示されるテキストを)"
ms.assetid: 9d18e0e0-f17f-4074-837d-e67ceeeaa89d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Windows フォーム コントロールに表示するテキストをデザイナーで設定する
通常、Windows フォーム コントロールは、コントロールの主要な機能に関連したテキストを表示します。  たとえば、<xref:System.Windows.Forms.Button> コントロールは通常、ボタンがクリックされたときに実行されるアクションを示すキャプションを表示します。  どのコントロールでも、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用することでテキストを設定したり返したりできます。  フォントは <xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して変更できます。  
  
### デザイナーを使ってテキストとフォントを設定するには  
  
1.  \[プロパティ\] ウィンドウで、コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティを適切な文字列に設定します。  
  
     下線の付いたショートカット キーを作成する場合は、ショートカット キーとして使用する文字の前にアンパサンド \(&\) を含めます。  
  
2.  \[プロパティ\] ウィンドウで、<xref:System.Windows.Forms.Control.Font%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
     標準のフォントのダイアログ ボックスで、使用するフォント、フォント スタイル、サイズ、文字飾り \(取り消し線、下線など\)、およびスクリプトを選択します。  
  
## 参照  
 [方法 : Windows フォーム コントロールによって表示されるテキストを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [フォントとテキストの使用](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)