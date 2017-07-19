---
title: "方法 :デザイナーを使って Windows フォーム ListView コントロールに列を追加する | Microsoft Docs"
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
  - "列 [Windows フォーム], 追加 (ListView コントロールに)"
  - "ListView コントロール [Windows フォーム], 追加 (列ヘッダーを)"
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 :デザイナーを使って Windows フォーム ListView コントロールに列を追加する
Windows フォームの <xref:System.Windows.Forms.ListView> コントロールでは、**詳細**ビューの場合、各リスト項目に対して複数の列を表示できます。  複数の列を使用することにより、リストの各項目に関して何種類かの情報を表示できます。  たとえば、ファイル リストに、ファイル名、ファイルの種類、サイズ、およびファイルの最終更新日を表示できます。  作成後に列に情報を設定する方法の詳細については、「[方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)」を参照してください。  
  
 次の手順では、<xref:System.Windows.Forms.ListView> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーで列を追加するには  
  
1.  **\[プロパティ\]** ウィンドウで、コントロールの <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View> に設定します。  
  
2.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.ListView.Columns%2A> プロパティの横にある**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
     **ColumnHeader コレクション エディター**が表示されます。  
  
3.  新しい列を追加するには、**\[追加\]** をクリックします。  次に、列ヘッダーを選択し、列ヘッダーのテキスト \(列のキャプション\)、テキストの配置、および幅を設定します。  
  
## 参照  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)