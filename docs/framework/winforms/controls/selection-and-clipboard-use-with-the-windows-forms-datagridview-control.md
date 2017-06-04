---
title: "Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用 | Microsoft Docs"
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
  - "セル, 選択 (グリッドの)"
  - "クリップボードのトピック, DataGridView コントロール内の"
  - "データ グリッド, 選択 (セルを)"
  - "DataGridView コントロール [Windows フォーム], クリップボードの使用"
  - "DataGridView コントロール [Windows フォーム], 選択 (セルを)"
  - "選択, DataGridView コントロール内の"
ms.assetid: 82cffcad-8b30-4897-bddb-c3a79d751b83
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用
`DataGridView` コントロールには、セル、行、および列をユーザーが選択する方法を設定するさまざまなオプションが用意されています。  たとえば、単一選択または複数選択を有効にしたり、ユーザーがセルをクリックした場合に行全体または列全体が選択されるようにしたり、ユーザーがヘッダーをクリックした場合にだけ行全体または列全体が選択されるようにしてセル単位での選択も有効にしたりできます。  選択操作のための独自のユーザー インターフェイスを提供する必要がある場合は、通常の選択操作を無効にし、すべての選択をプログラムで処理できます。  また、選択されている値をクリップボードにコピーできるようにすることもできます。  
  
## このセクションの内容  
 [Windows フォーム DataGridView コントロールの選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)  
 コントロール内でのユーザーおよびプログラムによる選択のオプションについて説明します。  
  
 [方法 : Windows フォーム DataGridView コントロールの選択モードを設定する](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)  
 ユーザーがセルをクリックしたときに単一の行が選択されるようにコントロールを構成する方法について説明します。  
  
 [方法 : Windows フォーム DataGridView コントロールの選択されたセル、行、および列を取得する](../../../../docs/framework/winforms/controls/selected-cells-rows-and-columns-datagridview.md)  
 選択されているセル、行、および列のコレクションを操作する方法について説明します。  
  
 [方法 : ユーザーが、Windows フォーム DataGridView コントロールからクリップボードに複数のセルをコピーできるようにする](../../../../docs/framework/winforms/controls/enable-users-to-copy-multiple-cells-to-the-clipboard-datagridview.md)  
 コントロールのクリップボード サポートを有効にする方法について説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView> コントロールの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=fullName>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> プロパティの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A> プロパティの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection>  
 <xref:System.Windows.Forms.DataGridViewSelectedCellCollection> クラスの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection>  
 <xref:System.Windows.Forms.DataGridViewSelectedRowCollection> クラスの参照ドキュメントを提供します。  
  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection>  
 <xref:System.Windows.Forms.DataGridViewSelectedColumnCollection> クラスの参照ドキュメントを提供します。  
  
## 参照  
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)