---
title: "方法 : 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する"
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
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b8fc8774e1f861db989b05678235ea34e38318c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>方法 : 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する
次のコード例は、アウトラインまたは枠線を作成する方法を示します、<xref:System.Windows.Forms.RichTextBox>コントロール。 例では、設定の値、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Padding>を 5 にセットのプロパティ、<xref:System.Windows.Forms.Control.Dock%2A>子のプロパティ<xref:System.Windows.Forms.RichTextBox>に制御を<xref:System.Windows.Forms.DockStyle.Fill>です。 <xref:System.Windows.Forms.Control.BackColor%2A>の<xref:System.Windows.Forms.Panel>コントロールに設定されている<xref:System.Drawing.Color.Blue%2A>、青色の枠を作成する、<xref:System.Windows.Forms.RichTextBox>コントロール。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Padding>  
 [Windows フォーム コントロールでのマージンと埋め込み](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
