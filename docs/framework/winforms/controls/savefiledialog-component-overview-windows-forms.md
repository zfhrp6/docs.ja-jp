---
title: "SaveFileDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "SaveFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "[ファイルの保存] ダイアログ ボックス, 表示"
  - "SaveFileDialog コンポーネント, SaveFileDialog の概要"
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# SaveFileDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.SaveFileDialog> コンポーネントは、定義済みのダイアログ ボックスです。  このダイアログ ボックスは、Windows で使用される標準の **\[ファイルの保存\]** ダイアログ ボックスと同じダイアログ ボックスです。  このコンポーネントは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。  
  
## SaveFileDialog コンポーネントの操作  
 このコントロールは、独自のダイアログ ボックスを設定せずにファイルの保存を行うための簡易ソリューションとして使用します。  Windows の標準のダイアログ ボックスを使用して、一般的な基本機能を持つアプリケーションを作成できます。  ただし、<xref:System.Windows.Forms.SaveFileDialog> コンポーネントを使用する場合は、独自のファイル保存ロジックを記述する必要があります。  
  
 実行時にダイアログ ボックスを表示するには、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用します。  <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> メソッドを使用して、ファイルを読み取り\/書き込みモードで開くことができます。  
  
 フォームに登録すると、<xref:System.Windows.Forms.SaveFileDialog> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.SaveFileDialog>   
 [SaveFileDialog コンポーネント](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)