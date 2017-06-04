---
title: "ListView コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ListView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "リスト ビュー"
  - "一覧"
  - "ListView コントロール [Windows フォーム], ListView コントロールの概要"
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ListView コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ListView> コントロールは、項目をアイコンと一緒に一覧表示します。  リスト ビューを使用すると、Windows エクスプローラーの右側のペインのようなユーザー インターフェイスを作成できます。  このコントロールには、LargeIcon、SmallIcon、List、Details の 4 つのビュー モードがあります。  
  
## ListView コントロールで可能なこと  
  
> [!NOTE]
>  新しく追加されたビュー モードである、並べて表示モードは、Windows XP と Windows Server 2003 の各オペレーティング システムでのみ使用できます。  詳細については、「[方法 : Windows フォーム ListView コントロールの "並べて表示" ビューを有効にする](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)」を参照してください。  
  
 LargeIcon モードでは、項目のテキストのそばに大きなアイコンが表示されます。コントロールが十分に大きい場合は、項目が複数の列に表示されます。  SmallIcon モードは、表示されるアイコンが小さい点を除けば LargeIcon モードと同じです。  List モードでは、小さなアイコンが表示されますが、項目は必ず 1 列で表示されます。  Details モードでは、各項目に関する情報が複数の列に表示されます。  詳細については、「[方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)」を参照してください。  ビュー モードは、<xref:System.Windows.Forms.ListView.View%2A> プロパティによって決定されます。  いずれのモードでも、イメージ リストのイメージを表示できます。  詳細については、「[方法 : Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)」を参照してください。  
  
 次の表では、<xref:System.Windows.Forms.ListView> のメンバーの一部およびそれらが有効であるビューを一覧しています。  
  
|ListView メンバー|ビュー|  
|-------------------|---------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> プロパティ|<xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> プロパティ|<xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> メソッド|<xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> プロパティ|<xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> イベント|<xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッド|<xref:System.Windows.Forms.View>、<xref:System.Windows.Forms.View>、または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッド|<xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> メソッド|<xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> プロパティ|<xref:System.Windows.Forms.View> 以外のすべてのビュー|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> プロパティ|<xref:System.Windows.Forms.View>.|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> プロパティ|<xref:System.Windows.Forms.View>、<xref:System.Windows.Forms.View>、または <xref:System.Windows.Forms.View>|  
  
 <xref:System.Windows.Forms.ListView> コントロールの主要プロパティは <xref:System.Windows.Forms.ListView.Items%2A> です。このプロパティは、コントロールによって表示される項目を保持します。  <xref:System.Windows.Forms.ListView.SelectedItems%2A> プロパティは、コントロールで現在選択されている項目を保持します。  <xref:System.Windows.Forms.ListView.MultiSelect%2A> プロパティが `true` に設定されている場合、ユーザーは複数の項目を選択できます。たとえば、一度に複数の項目を別のコントロールにドラッグ アンド ドロップできます。  <xref:System.Windows.Forms.ListView.CheckBoxes%2A> プロパティが `true` に設定されている場合、<xref:System.Windows.Forms.ListView> コントロールでは、項目の横にチェック ボックスを表示できます。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A> プロパティは、リスト内の項目をアクティブにするためにユーザーが実行する必要のある操作を決定します。指定できるオプションは、<xref:System.Windows.Forms.ItemActivation>、<xref:System.Windows.Forms.ItemActivation>、および <xref:System.Windows.Forms.ItemActivation> です。  アクティブ化する操作が <xref:System.Windows.Forms.ItemActivation> の場合、項目をアクティブにするにはシングル クリックする必要があります。  <xref:System.Windows.Forms.ItemActivation> の場合は、項目をアクティブにするには、ダブルクリックする必要があります。シングル クリックすると、項目テキストの色が変わります。  <xref:System.Windows.Forms.ItemActivation> の場合は、項目をアクティブにするには、ダブルクリックする必要がありますが、外観は変わりません。  
  
 <xref:System.Windows.Forms.ListView> コントロールでは、グループ化、並べて表示ビュー、挿入マークなど、Windows XP プラットフォームで使用できる visual スタイルなどの機能もサポートされています。  詳細については、「[Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/ja-jp/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロール内の項目を選択する](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールの項目をグループ化する](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールに挿入マークを表示する](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)   
 [方法 : ListView コントロールに検索機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [方法 : Windows フォームでマルチペイン ユーザー インターフェイスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)