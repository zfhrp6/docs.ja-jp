---
title: '方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], for controls
- examples [Windows Forms], tooltips
ms.assetid: c4b60637-4c0a-44c2-a103-f66dff887936
ms.openlocfilehash: 4e4623c1c0fe7d082e4d1a1f404ddaa94e79fc2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time"></a>方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する
設定することができます、<xref:System.Windows.Forms.ToolTip>コード内、または Windows フォーム デザイナーでの文字列。 詳細については、<xref:System.Windows.Forms.ToolTip>コンポーネントを参照してください[ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-set-a-tooltip-programmatically"></a>ツールヒントをコードから設定するには  
  
1.  ツールヒントを表示するコントロールを追加します。  
  
2.  使用して、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>のメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネントです。  
  
    ```vb  
    ' In this example, Button1 is the control to display the ToolTip.  
    ToolTip1.SetToolTip(Button1, "Save changes")  
    ```  
  
    ```csharp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1.SetToolTip(button1, "Save changes");  
    ```  
  
    ```cpp  
    // In this example, button1 is the control to display the ToolTip.  
    toolTip1->SetToolTip(button1, "Save changes");  
    ```  
  
### <a name="to-set-a-tooltip-in-the-designer"></a>デザイナーでツールヒントを設定するには  
  
1.  フォームに <xref:System.Windows.Forms.ToolTip> コンポーネントを追加します。  
  
2.  ツールヒントを表示またはフォームに追加されるコントロールを選択します。  
  
3.  **プロパティ**ウィンドウで、設定、 **ToolTip1 のツールヒント**をテキストの適切な文字列値です。  
  
## <a name="see-also"></a>関連項目  
 [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)  
 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
