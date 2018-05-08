---
title: '方法 : ToolStrip を ToolStripContainer からフォームに移動する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 6cc54264033eca541ce845b75d608087fee8a542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>方法 : ToolStrip を ToolStripContainer からフォームに移動する
移動する、次の手順を使用して、<xref:System.Windows.Forms.ToolStrip>のうち、<xref:System.Windows.Forms.ToolStripContainer>からフォームにします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>ToolStrip を ToolStripContainer からフォームに不足を移動するには  
  
1.  <xref:System.Windows.Forms.ToolStrip> を選択します。  
  
2.  切り取り、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら X キーを押すかを右クリックし、<xref:System.Windows.Forms.ToolStrip>選択**切り取り**コンテキスト メニューからです。  
  
3.  フォームを選択します。  
  
4.  貼り付け、<xref:System.Windows.Forms.ToolStrip>で ctrl キーを押しながら V キーを押すかを選択して**貼り付け**から、**編集**メニュー。  
  
5.  設定、<xref:System.Windows.Forms.ToolStrip.Dock%2A>のプロパティ、<xref:System.Windows.Forms.ToolStrip>に**上部**です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
