---
title: StatusBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 6dd5b45b38ec4fb04d9a53a1648cfe6e5a5b9f20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535130"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
 Windows フォーム[StatusBar コントロール](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md)はフォーム上の領域で、通常、アプリケーションがさまざまな種類のステータス情報を表示できます、ウィンドウの下部に表示として使用します。 <xref:System.Windows.Forms.StatusBar> コントロールがテキストまたは状態、または一連のプロセスが動作してを示すアニメーションのアイコンを示すアイコンを表示してステータス バー パネルを持つことができます。たとえば、[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]ドキュメントが保存されていることを示します。  
  
## <a name="using-the-statusbar-control"></a>StatusBar コントロールの使用  
 Internet Explorer では、ステータス バーを使用して、ハイパーリンク; に、マウスでロール オーバー時に、ページの URL を示します[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]での情報がページの場所、セクションの場所、および上書きとリビジョンの追跡や Visual Studio は使用して、ステータス バーをドッキング可能ウィンドウを操作する方法を示すなどの状況に応じた情報などの編集モードドッキングまたはフローティングです。  
  
 ステータス バーに設定して、1 つのメッセージを表示することができます、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`false`(既定) と設定、<xref:System.Windows.Forms.StatusBar.Text%2A>ステータス バーにステータス バーに表示するテキストのプロパティです。 ステータス バーを設定して複数の 1 種類の情報を表示するパネルに分割することができます、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`true`を使用して、<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>メソッドの<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [方法: Windows フォームの StatusBar コントロールでクリックされたパネルを確認する](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)
