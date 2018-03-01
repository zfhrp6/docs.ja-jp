---
title: "ListView コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b79fecb0a537f4c568b4a57e9ce2bfab8d8e1005
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="listview-control-overview-windows-forms"></a>ListView コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ListView> コントロールにはアイコン表示で項目の一覧が表示されます。 リスト ビューを使用すると、Windows エクスプローラーの右側のペインのようなユーザー インターフェイスを作成することができます。 コントロールが 4 つの表示モード: LargeIcon、SmallIcon、リスト、および詳細。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView コントロールに行うことができます。  
  
> [!NOTE]
>  タイルで、追加の表示モードは Windows XP および Windows Server 2003 オペレーティング システムではできるだけです。 詳細については、次を参照してください。[する方法: Windows フォーム ListView コントロールの並べて表示ビューを有効にする](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md)です。  
  
 LargeIcon モードには、項目のテキストの横にある大きいアイコンが表示されます。項目は、コントロールが十分な大きさである場合に、複数の列に表示されます。 SmallIcon モードでは、小さいアイコンを表示する点を除いて同じです。 一覧モードでは、小さいアイコンが表示されますは常に 1 つの列であります。 詳細モードでは、複数の列に項目が表示されます。 詳細については、「[する方法: Windows フォーム ListView コントロール列の追加](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)です。 表示モードはによって決定されます、<xref:System.Windows.Forms.ListView.View%2A>プロパティです。 イメージ リストのイメージの表示モードがすべて表示できます。 詳細については、「[する方法: Windows フォーム ListView コントロールの表示アイコン](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)です。  
  
 次の表の一覧、<xref:System.Windows.Forms.ListView>メンバーおよびで有効であるビューです。  
  
|ListView のメンバー|表示|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> メソッド|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> プロパティ|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> イベント|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッド|<xref:System.Windows.Forms.View.Details>、 <xref:System.Windows.Forms.View.List>、または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッド|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> メソッド|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> プロパティ|除くすべてのビュー<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> プロパティ|<xref:System.Windows.Forms.View.Details>。|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> プロパティ|<xref:System.Windows.Forms.View.LargeIcon>、 <xref:System.Windows.Forms.View.SmallIcon>、または <xref:System.Windows.Forms.View.Tile>|  
  
 キー プロパティ、<xref:System.Windows.Forms.ListView>コントロールが<xref:System.Windows.Forms.ListView.Items%2A>、コントロールによって表示される項目が含まれています。 <xref:System.Windows.Forms.ListView.SelectedItems%2A>プロパティには、コントロールで現在選択されている項目のコレクションが含まれています。 ユーザーがドラッグ アンド場合、別のコントロールには、一度にいくつかの項目をドロップする例については、複数の項目を選択できる、<xref:System.Windows.Forms.ListView.MultiSelect%2A>プロパティに設定されている`true`です。 <xref:System.Windows.Forms.ListView>場合、コントロールは、項目の横にチェック ボックスを表示できます、<xref:System.Windows.Forms.ListView.CheckBoxes%2A>プロパティに設定されている`true`です。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A>プロパティは、アクションの種類、ユーザーは、リスト内の項目をアクティブに実行する必要がありますを決定します。 オプションは、 <xref:System.Windows.Forms.ItemActivation.Standard>、 <xref:System.Windows.Forms.ItemActivation.OneClick>、と<xref:System.Windows.Forms.ItemActivation.TwoClick>。 <xref:System.Windows.Forms.ItemActivation.OneClick>アクティブ化には、シングル クリックで項目をアクティブ化が必要です。 <xref:System.Windows.Forms.ItemActivation.TwoClick>アクティブ化をダブルクリックすると、アイテムをアクティブ化ユーザーが必要です。1 回のクリックでは、項目のテキストの色を変更します。 <xref:System.Windows.Forms.ItemActivation.Standard>アクティブ化をダブルクリックすると、アイテムをアクティブ化ユーザーが必要ですが、アイテムの外観は変わりません。  
  
 <xref:System.Windows.Forms.ListView>コントロールもサポートしている visual スタイルと使用できるその他の機能グループ化、並べて表示ビュー、および挿入マークを含む、Windows XP のプラットフォームでします。 詳細については、次を参照してください。 [Windows XP の機能と Windows フォーム コントロール](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ListView>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [方法: Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロール内の項目を選択する](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールの項目をグループ化する](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)  
 [方法: Windows フォーム ListView コントロールに挿入マークを表示する](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)  
 [方法: ListView コントロールに検索機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
 [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)
