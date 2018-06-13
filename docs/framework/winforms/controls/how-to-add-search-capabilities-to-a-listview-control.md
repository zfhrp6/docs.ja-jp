---
title: '方法 : ListView コントロールに検索機能を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: 2049638998f7a8d099e14fab9c95384a49c67833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528283"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>方法 : ListView コントロールに検索機能を追加する
内の項目の大規模な一覧を使用する場合に多くの場合、<xref:System.Windows.Forms.ListView>をユーザーに検索機能を提供するコントロール。 <xref:System.Windows.Forms.ListView>コントロールは、次の 2 つの異なる方法でこの機能を提供しています。 テキストに一致すると、場所を検索します。  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドでは、フルテキスト検索を実行することができます、<xref:System.Windows.Forms.ListView>リスト ビューまたは詳細ビューで、指定された検索文字列と省略可能な開始と終了インデックス。 これに対し、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>メソッド内の項目を見つけることができます、<xref:System.Windows.Forms.ListView>アイコンまたはタイル ビューで、一連の x 座標と y 座標と検索する方向を指定します。  
  
### <a name="to-find-an-item-using-text"></a>テキストを使用して項目を検索するには  
  
1.  作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.ListView.View%2A>プロパティに設定<xref:System.Windows.Forms.View.Details>または<xref:System.Windows.Forms.View.List>、および設定し、<xref:System.Windows.Forms.ListView>項目を含むです。  
  
2.  呼び出す、<xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドを検索するには、項目のテキストを渡すことです。  
  
3.  次のコード例は、基本的なを作成する方法を示します<xref:System.Windows.Forms.ListView>項目では、設定、およびユーザーからのテキスト入力一覧の項目の検索を使用しています。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>X 座標と y 座標を使用して項目を検索するには  
  
1.  作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.View>プロパティに設定<xref:System.Windows.Forms.View.SmallIcon>または<xref:System.Windows.Forms.View.LargeIcon>、および設定し、<xref:System.Windows.Forms.ListView>項目を含むです。  
  
2.  呼び出す、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>を渡し、必要な x 座標と y 座標を検索したい方向メソッドです。  
  
3.  次のコード例は、基本的なアイコンを作成する方法を示します<xref:System.Windows.Forms.ListView>、そこに項目、およびキャプチャ、<xref:System.Windows.Forms.Control.MouseDown>上で最も近い項目を検索するイベントです。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [方法: Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
