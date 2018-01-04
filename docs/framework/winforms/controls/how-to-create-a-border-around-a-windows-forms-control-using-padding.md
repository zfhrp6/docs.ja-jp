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
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="b441d-102">方法 : 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する</span><span class="sxs-lookup"><span data-stu-id="b441d-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="b441d-103">次のコード例は、アウトラインまたは枠線を作成する方法を示します、<xref:System.Windows.Forms.RichTextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b441d-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="b441d-104">例では、設定の値、<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Padding>を 5 にセットのプロパティ、<xref:System.Windows.Forms.Control.Dock%2A>子のプロパティ<xref:System.Windows.Forms.RichTextBox>に制御を<xref:System.Windows.Forms.DockStyle.Fill>です。</span><span class="sxs-lookup"><span data-stu-id="b441d-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="b441d-105"><xref:System.Windows.Forms.Control.BackColor%2A>の<xref:System.Windows.Forms.Panel>コントロールに設定されている<xref:System.Drawing.Color.Blue%2A>、青色の枠を作成する、<xref:System.Windows.Forms.RichTextBox>コントロール。</span><span class="sxs-lookup"><span data-stu-id="b441d-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b441d-106">例</span><span class="sxs-lookup"><span data-stu-id="b441d-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b441d-107">参照</span><span class="sxs-lookup"><span data-stu-id="b441d-107">See Also</span></span>  
 <xref:System.Windows.Forms.Padding>  
 [<span data-ttu-id="b441d-108">Windows フォーム コントロールでのマージンと埋め込み</span><span class="sxs-lookup"><span data-stu-id="b441d-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)
