---
title: "方法 : ToolStrip コントロールにトグル ボタンを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.ToolStripButton>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
