---
title: "方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する | Microsoft Docs"
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
  - "グループ化"
  - "グループ, Windows フォーム コントロールの"
  - "ListView コントロール [Windows フォーム], グループ化 (項目を)"
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する
<xref:System.Windows.Forms.ListView> コントロールのグループ化機能を使用すると、関連する複数の項目をグループ化して表示できます。  これらのグループは、画面上で、グループ タイトルを含む水平方向のグループ ヘッダーで区切られます。  <xref:System.Windows.Forms.ListView> グループを使って、項目をアルファベット順、日付順、またはその他の論理的なグループにまとめることにより、大きなリストの内部を移動することが簡単になります。  次のイメージは、グループ化した項目の例を示しています。  
  
 ![ListView グループ](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 次の手順では、<xref:System.Windows.Forms.ListView> コントロールが含まれているフォームを持つ **Windows アプリケーション** プロジェクトが必要です。  このプロジェクトの設定の詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」および「[方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)」を参照してください。  
  
 グループ化を有効にするには、まず、デザイナーまたはプログラムで、1 つ以上の <xref:System.Windows.Forms.ListViewGroup> オブジェクトを作成します。  グループを定義した後で、それに項目を割り当てることができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> を [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドを呼び出した場合だけです。  以前のオペレーティング システムでは、グループに関連するコードは無効になり、グループは表示されません。  詳細については、「<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイナーでグループを追加または削除するには  
  
1.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.ListView.Groups%2A> プロパティの横にある**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
     **ListViewGroup コレクション エディター**が表示されます。  
  
2.  グループを追加するには、**\[追加\]** をクリックします。  新規グループのプロパティ、たとえば <xref:System.Windows.Forms.ListViewGroup.Header%2A> プロパティや <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> プロパティなどを設定します。  グループを削除するには、項目を選択し、**\[削除\]** をクリックします。  
  
### デザイナーでグループに項目を割り当てるには  
  
1.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.ListView.Items%2A> プロパティの横にある**省略記号** \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) ボタンをクリックします。  
  
     **ListViewItem コレクション エディター**が表示されます。  
  
2.  項目を追加するには、**\[追加\]** をクリックします。  新規項目のプロパティ、たとえば <xref:System.Windows.Forms.ListViewItem.Text%2A> プロパティや <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> プロパティなどを設定します。  
  
3.  <xref:System.Windows.Forms.ListViewItem.Group%2A> プロパティをクリックして、ドロップダウン リストからグループを選択します。  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/ja-jp/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)