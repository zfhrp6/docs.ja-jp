---
title: "方法 : デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する | Microsoft Docs"
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
  - "ListView コントロール [Windows フォーム], 追加 (リスト項目を)"
  - "ListView コントロール [Windows フォーム], データの読み込み"
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する
Windows フォームの <xref:System.Windows.Forms.ListView> コントロールに項目を追加するには、項目を指定し、その項目にプロパティを割り当てます。  リスト項目の追加または削除は、いつでも実行できます。  
  
 次の手順では、<xref:System.Windows.Forms.ListView> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーを使って項目を追加または削除するには  
  
1.  <xref:System.Windows.Forms.ListView> コントロールを選択します。  
  
2.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.ListView.Items%2A> プロパティの横にある**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
     **ListViewItem コレクション エディター**が表示されます。  
  
3.  項目を追加するには、**\[追加\]** をクリックします。  新規項目のプロパティ、たとえば <xref:System.Windows.Forms.ListView.Text%2A> プロパティや <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> プロパティなどを設定します。  
  
4.  項目を削除するには、項目を選択し、**\[削除\]** をクリックします。  
  
## 参照  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [方法 : Windows フォーム ListView コントロールの項目をグループ化する](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)