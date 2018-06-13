---
title: '方法 : ContextMenuStrip のオープン イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: c5af03f4726063754f81ec9226b4b161599b4121
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531863"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>方法 : ContextMenuStrip のオープン イベントを処理する
動作をカスタマイズすることができます、<xref:System.Windows.Forms.ContextMenuStrip>処理によって制御、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。  
  
## <a name="example"></a>例  
 次のコード例は、処理する方法を示します、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。 イベント ハンドラーが動的に項目を追加、<xref:System.Windows.Forms.ContextMenuStrip>コントロール。 完全なコード例は、次を参照してください。[する方法: ToolStrip の項目を動的に追加](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md)です。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>プロパティを`true`して、メニューを開かないようにします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
