---
title: "ToolBar コントロールの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eac54e18f397cf455ffd5fa33c2e000d87b917a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム <xref:System.Windows.Forms.ToolBar> コントロールは、コマンドをアクティブ化するドロップダウン メニューとビットマップのボタンの行を表示するコントロール バーとしてフォームを使用します。 そのため、ツールバー ボタンをクリックすることは、メニュー コマンドを選択することと同じです。 ボタンは、プッシュ ボタン、ドロップダウン メニュー、または区切りとして表示して機能するように構成できます。 通常、ツールバーには、アプリケーションのメニュー構造の項目に対応するボタンとメニューが含まれ、アプリケーションで最も頻繁に使用される関数やコマンドにすばやくアクセスできます。  
  
## <a name="working-with-the-toolbar-control"></a>ToolBar コントロールの操作  
 A<xref:System.Windows.Forms.ToolBar>コントロールは、通常「ドッキング」、その親ウィンドウの上部にあるが、ウィンドウの任意の辺にもドッキングできます。 ツール バー ボタンをマウス ポインターでポイントすると、ツールヒントが表示されます。 ツールヒントは、ボタンやメニューの目的を簡単に説明する小さなポップアップ ウィンドウです。 ツールヒントを表示する、<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A>プロパティに設定する必要があります`true`です。  
  
> [!NOTE]
>  特定のアプリケーション機能のコントロールは、アプリケーション ウィンドウの上に "フローティング" して位置変更できるツールバーとよく似ています。 Windows フォームのツール バー コントロールでは、このような操作を実行できません。  
  
 ときに、<xref:System.Windows.Forms.ToolBar.Appearance%2A>プロパティに設定されている<xref:System.Windows.Forms.ToolBarAppearance>、発生し、3 次元、ツールバーのボタンが表示されます。 設定することができます、<xref:System.Windows.Forms.ToolBar.Appearance%2A>ツールバーのプロパティ<xref:System.Windows.Forms.ToolBarAppearance>ツールバーとそのボタンの外観フラットです。 フラットなボタンにマウス ポインターを置くと、ボタンは 3 次元表示に変わります。 ツール バー ボタンは、区切りを使用すると論理グループに分けることができます。 区切り記号がツール バー ボタンで、<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティに設定<xref:System.Windows.Forms.ToolBarButtonStyle>です。 区切りは、ツール バー上の空スペースとして表示されます。 ツール バーはフラットに表示され、ボタンの区切りは、ボタンの間にスペースを入れて表示されるのではなく線として表示されます。  
  
 <xref:System.Windows.Forms.ToolBar>コントロールでは、ツールバーを追加することで作成できます。<xref:System.Windows.Forms.Button>オブジェクトを、<xref:System.Windows.Forms.ToolBar.Buttons%2A>コレクション。 ボタンを追加するコレクション エディターを使用することができます、<xref:System.Windows.Forms.ToolBar>コントロール; 各<xref:System.Windows.Forms.Button>オブジェクトがテキストまたはイメージが割り当てられて、両方を割り当てることはできます。 イメージは、関連付けられた [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) コンポーネントから取得されます。 実行時に、追加または削除できますからボタン、<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>を使用して、<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A>と<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>メソッドです。 プログラムのボタンを<xref:System.Windows.Forms.ToolBar>、コードを追加、<xref:System.Windows.Forms.ToolBar.ButtonClick>のイベント、<xref:System.Windows.Forms.ToolBar>を使用して、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A>のプロパティ、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>クリックしてされたボタンを決めるクラスをします。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ToolBar>  
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [方法: ツール バー コントロールにボタンを追加する](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [方法: ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [方法: ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
