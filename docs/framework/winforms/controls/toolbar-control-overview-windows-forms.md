---
title: "ToolBar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ToolBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ToolBar コントロール [Windows フォーム], ToolBar コントロールの概要"
  - "ツール バー [Windows フォーム], ツール バーの概要"
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# ToolBar コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォームの <xref:System.Windows.Forms.ToolBar> コントロールは、一連のドロップダウン メニューやコマンド実行用のビットマップ ボタンを表示する、フォーム上のコントロール バーとして使用します。  ツール バーのボタンをクリックして、メニュー コマンドを選択するのと同じ操作ができます。  ボタンは、プッシュ ボタン、ドロップダウン メニュー、または区切り記号として機能するように設定できます。  通常、ツール バーのボタンとメニューは、アプリケーションのメニュー構造の項目に対応し、使用頻度の高い関数やコマンドをすばやく実行します。  
  
## ToolBar コントロールの操作  
 <xref:System.Windows.Forms.ToolBar> コントロールは、通常は親ウィンドウの上部に沿って "ドッキング" されますが、ウィンドウの上下左右のどこにでもドッキングできます。  ツール バーには、ユーザーがツール バー ボタンをマウス ポインターでポイントしたときに表示されるツール ヒントを実装できます。  ツール ヒントは、ボタンまたはメニューの用途を簡潔に説明するための、小さなポップアップ ウィンドウです。  ツールヒントを表示するには、<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> プロパティに `true` を設定します。  
  
> [!NOTE]
>  一部のアプリケーションには、アプリケーション ウィンドウの上部に "浮遊" していて位置を変更できる、ツール バーによく似たコントロールがあります。  Windows フォームの ToolBar コントロールは、位置を変更できません。  
  
 <xref:System.Windows.Forms.ToolBar.Appearance%2A> プロパティに [Normal](frlrfSystemWindowsFormsToolBarAppearanceClassTopic) を設定すると、ツール バー ボタンが立体的に表示されます。  ツール バーの <xref:System.Windows.Forms.ToolBar.Appearance%2A> プロパティに <xref:System.Windows.Forms.ToolBarAppearance> を設定すると、ツール バーとボタンが平面的に表示されます。  平面表示されたボタンの上にマウス ポインターが置かれると、ボタンが立体的に表示されます。  ツール バー ボタンは、区切り記号で論理的なグループに分類できます。  区切り記号は、<xref:System.Windows.Forms.ToolBarButton.Style%2A> プロパティに [Separator](frlrfSystemWindowsFormsToolBarButtonStyleClassTopic) を設定したツール バー ボタンです。  ツール バー上では空の領域として表示されます。  ツール バーが平面表示されているときは、ボタン区切り記号は空の領域ではなく線で表示されます。  
  
 <xref:System.Windows.Forms.ToolBar> コントロールでは、<xref:System.Windows.Forms.Button> オブジェクトを <xref:System.Windows.Forms.ToolBar.Buttons%2A> コレクションに追加することにより、ツール バーを作成できます。  ボタンを <xref:System.Windows.Forms.ToolBar> コントロールに追加するときには、コレクション エディターを使用できます。各 <xref:System.Windows.Forms.Button> オブジェクトには、テキストまたはイメージを割り当てます \(両方を割り当てることもできます\)。  イメージは、関連付けられた [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) コンポーネントによって提供されます。  実行時に <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> メソッドや <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> メソッドを使用して、<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> にボタンを登録したり、登録済みのボタンを削除したりできます。  <xref:System.Windows.Forms.ToolBar> のボタンをプログラミングするには、<xref:System.Windows.Forms.ToolBar> の <xref:System.Windows.Forms.ToolBar.ButtonClick> イベントにコードを追加します。クリックされたボタンの判別には、<xref:System.Windows.Forms.ToolBarButtonClickEventArgs> クラスの <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> プロパティを使用します。  
  
## 参照  
 <xref:System.Windows.Forms.ToolBar>   
 [ToolBar コントロール](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)   
 [方法 : ツール バー コントロールにボタンを追加する](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)   
 [方法 : ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)   
 [方法 : ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)