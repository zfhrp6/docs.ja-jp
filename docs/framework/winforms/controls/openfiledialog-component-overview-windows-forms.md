---
title: "OpenFileDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "OpenFileDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "[ファイルを開く] ダイアログ ボックス, 表示 (Windows フォームで)"
  - "OpenFileDialog コンポーネント, OpenFileDialog の概要"
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# OpenFileDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.OpenFileDialog> コンポーネントは、定義済みのダイアログ ボックスです。  Windows オペレーティング システムの **\[ファイルを開く\]** ダイアログ ボックスと同じダイアログ ボックスです。  このコンポーネントは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。  
  
## このコンポーネントの使用  
 このコンポーネントは、独自のダイアログ ボックスを使用せずにファイル選択を行うための簡易ソリューションとして、Windows ベースのアプリケーション内で使用できます。  Windows の標準のダイアログ ボックスを使用して、一般的な基本機能を持つアプリケーションを作成できます。  ただし、<xref:System.Windows.Forms.OpenFileDialog> コンポーネントを使用する場合は、独自のファイル オープン ロジックを記述する必要があります。  
  
 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用して、実行時にダイアログを表示します。  <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> プロパティを使用すると、複数のファイルを選択して開くことができます。  また、<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> プロパティを使用すると、読み取り専用で開くためのチェック ボックスをダイアログ ボックスに表示するかどうかを指定できます。  <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> プロパティは、読み取り専用チェック ボックスがオンかオフかを示します。  <xref:System.Windows.Forms.FileDialog.Filter%2A> プロパティは、現在のファイル名フィルター文字列を設定します。この文字列で、ダイアログ ボックスの "ファイルの種類" で表示される選択肢を設定します。  
  
 フォームに登録すると、<xref:System.Windows.Forms.OpenFileDialog> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.OpenFileDialog>   
 [OpenFileDialog コンポーネント](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)