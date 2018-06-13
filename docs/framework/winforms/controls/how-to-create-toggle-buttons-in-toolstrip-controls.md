---
title: '方法 : ToolStrip コントロールにトグル ボタンを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: a04d531433273328c2d8eb0c5ef614f08c33952a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530382"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a>方法 : ToolStrip コントロールにトグル ボタンを作成する
トグル ボタンをクリックすると、くぼみ表示され、ユーザーがボタンをもう一度クリックするまで、くぼみの外観を保持します。  
  
### <a name="to-create-a-toggling-toolstripbutton"></a>切り替え ToolStripButton を作成するには  
  
-   次のコード例のようなコードを使用します。 このコードは、フォームが含まれている前提としています。、<xref:System.Windows.Forms.ToolStrip>コントロール、およびその<xref:System.Windows.Forms.ToolStrip.Items%2A>コレクションが含まれています、<xref:System.Windows.Forms.ToolStripButton>と呼ばれる`toolStripButton1`です。 呼ばれるイベント ハンドラーを設定することも想定`toolStripButton1_CheckedChanged`です。  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStripButton>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
