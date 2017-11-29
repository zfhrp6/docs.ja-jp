---
title: "方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97c9dc3a12227d3c9bfd64c97be61e69b50d2bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>方法 : デザイナーを使って Windows フォーム ListView コントロールの項目をグループ化する
グループ化機能、<xref:System.Windows.Forms.ListView>コントロールでは、グループ内のアイテムの関連のセットを表示することができます。 これらのグループは、画面の水平方向のグループを含むヘッダーにグループのタイトルで区切られます。 使用することができます<xref:System.Windows.Forms.ListView>日付、またはその他の論理グループで、アルファベット順に項目をグループ化して簡単に大規模なリストを移動するグループです。 次の図は、いくつかのグループ化された項目を示します。  
  
 ![ListView グループ](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 次の手順が必要です、 **Windows アプリケーション**が含まれているフォーム プロジェクト、<xref:System.Windows.Forms.ListView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[する方法: Windows アプリケーション プロジェクトを作成](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)と[する方法: Windows フォームにコントロールを追加](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)です。  
  
 グループ化を有効にする必要があります最初に作成する 1 つまたは複数<xref:System.Windows.Forms.ListViewGroup>デザイナーで、またはプログラムでのオブジェクト。 グループを定義した後に項目を割り当てることができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView>のみ使用可能なグループ[!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)]、アプリケーションを呼び出すと、<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>メソッドです。 以前のオペレーティング システムでグループに関連するすべてのコードが影響を与えませんし、グループが表示されません。 詳細については、「<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-add-or-remove-groups-in-the-designer"></a>追加またはデザイナーでグループを削除するには  
  
1.  **プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Groups%2A>プロパティです。  
  
     **ListViewGroup コレクション エディター**が表示されます。  
  
2.  グループを追加するをクリックして、**追加**ボタンをクリックします。 など、新しいグループのプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewGroup.Header%2A>と<xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>プロパティです。 グループを削除するを選択し、クリックして、**削除**ボタンをクリックします。  
  
### <a name="to-assign-items-to-groups-in-the-designer"></a>項目をデザイナーでのグループに割り当てる  
  
1.  **プロパティ**ウィンドウで、をクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを<xref:System.Windows.Forms.ListView.Items%2A>プロパティです。  
  
     **ListViewItem コレクション エディター**が表示されます。  
  
2.  新しいアイテムを追加する をクリックして、**追加**ボタンをクリックします。 など、新しい項目のプロパティを設定することができますし、<xref:System.Windows.Forms.ListViewItem.Text%2A>と<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>プロパティです。  
  
3.  選択、<xref:System.Windows.Forms.ListViewItem.Group%2A>プロパティし、ドロップダウン リストからグループを選択します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP の機能と Windows フォーム コントロール](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [方法: Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
