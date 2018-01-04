---
title: "ToolBar コントロール (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 204c4229852d4e91d2af7a27163c7418b9a1e9b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-control-windows-forms"></a>ToolBar コントロール (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> コントロールは、`ToolBar` コントロールに代わると共に追加の機能を提供します。ただし、`ToolBar` コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム `ToolBar` コントロールは、コマンドをアクティブ化するドロップダウン メニューとビットマップのボタンの行を表示するコントロール バーとしてフォームを使用します。 そのため、ツールバー ボタンのクリックは、メニュー コマンドと同じです。 ボタンは、プッシュ ボタン、ドロップダウン メニュー、または区切り記号として表示して機能するように構成できます。 通常、ツールバーには、アプリケーションのメニュー構造の項目に対応するボタンとメニューが含まれ、アプリケーションで最も頻繁に使用される関数やコマンドにすばやくアクセスできます。  
  
> [!NOTE]
>  `ToolBar` コントロールの <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> プロパティは、<xref:System.Windows.Forms.ContextMenu> クラスのインスタンスを参照として取得します。 このプロパティは <xref:System.Windows.Forms.Menu> クラスから継承する任意のオブジェクトを受け入れるため、アプリケーションのツールバーにこの種類のボタンを実装する場合は、渡す参照を慎重に検討してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ToolBar コントロールの概要](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 ユーザーが操作できるカスタム ツールバーを設計できる、`ToolBar` コントロールの一般的な概念について説明します。  
  
 [方法: ツール バー コントロールにボタンを追加する](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 ボタンを `ToolBar` コントロールに追加する方法について説明します。  
  
 [方法: ツール バー ボタンのアイコンを定義する](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 アイコンを `ToolBar` コントロールのボタン内に表示する方法について説明します。  
  
 [方法: ツール バー ボタンのメニュー イベントをトリガーする](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 `ToolBar` コントロールでユーザーがクリックするボタンを解釈するコードの記述方法について説明します。  
  
 参照してください[する方法: ツールバー ボタンを使用して、デザイナーのアイコンを定義する](http://msdn.microsoft.com/library/ms233659\(v=vs.110\))、[する方法: ツールバー コントロールを使用して、デザイナーに追加のボタン](http://msdn.microsoft.com/library/ms233650\(v=vs.110\))です。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.ToolBar> クラス  
 クラスとそのメンバーに関するリファレンス情報を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。  
  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 Windows フォーム アプリケーションでメニュー、コントロール、およびユーザー コントロールをホストするツールバーについて説明します。
