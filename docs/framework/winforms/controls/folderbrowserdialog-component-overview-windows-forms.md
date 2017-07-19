---
title: "FolderBrowserDialog コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "FolderBrowserDialog"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ディレクトリ [Windows フォーム], 有効化 (アプリケーションで参照を)"
  - "FolderBrowserDialog コンポーネント [Windows フォーム], FolderBrowserDialog の概要"
  - "フォルダー [Windows フォーム], 有効化 (アプリケーションで参照を)"
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# FolderBrowserDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントは、フォルダーの参照と選択に使用されるモーダル ダイアログ ボックスです。  <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントから新規フォルダーを作成することもできます。  
  
> [!NOTE]
>  フォルダーではなくファイルを選択する場合は、[OpenFileDialog](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md) コンポーネントを使用します。  
  
 <xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントは、実行時に <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> メソッドを使用して表示されます。  <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> プロパティを設定して、ダイアログ ボックスのツリー ビューに表示される最上位フォルダーおよびサブフォルダーを指定します。  ダイアログ ボックスが表示された後は、<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> プロパティを使用して、選択されたフォルダーのパスを取得できます。  
  
 フォームに登録すると、<xref:System.Windows.Forms.FolderBrowserDialog> コンポーネントは Windows フォーム デザイナーの下部のトレイに表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [方法 : Windows フォーム FolderBrowserDialog コンポーネントを使用してフォルダーを選択する](../../../../docs/framework/winforms/controls/how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)   
 [FolderBrowserDialog コンポーネント](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)