---
title: "方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする"
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
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ea6d3615780c8def31b7dbdcf870020a106e80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a>方法 : Windows フォーム内で実行時に ToolStrip 項目を並べ替えできるようにする
再配置するユーザーを有効にすることができます<xref:System.Windows.Forms.ToolStripItem>コントロールに対して、<xref:System.Windows.Forms.ToolStrip>です。  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a>実行時に ToolStripItem 再配置を有効にするには  
  
-   <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> プロパティを `true` に設定します。 既定では、<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>は`false`します。  
  
     実行時に、ユーザーを押したまま、ALT キーを押し、マウスの左ボタンをドラッグする、<xref:System.Windows.Forms.ToolStripItem>で別の場所に、<xref:System.Windows.Forms.ToolStrip>です。  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>  
 [ToolStrip コントロールの概要](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip テクノロジの概要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
