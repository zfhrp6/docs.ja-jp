---
title: "方法 : 垂直方向のテキストを作成する"
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
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8615a90094232381f2c8d51f5593276d0c01f892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="67ce1-102">方法 : 垂直方向のテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="67ce1-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="67ce1-103">使用することができます、<xref:System.Drawing.StringFormat>テキストを水平方向にではなく垂直方向に描画することを指定するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="67ce1-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ce1-104">例</span><span class="sxs-lookup"><span data-stu-id="67ce1-104">Example</span></span>  
 <span data-ttu-id="67ce1-105">次の例は、値を割り当てます<xref:System.Drawing.StringFormatFlags.DirectionVertical>を<xref:System.Drawing.StringFormat.FormatFlags%2A>のプロパティ、<xref:System.Drawing.StringFormat>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="67ce1-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="67ce1-106">ある<xref:System.Drawing.StringFormat>にオブジェクトが渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="67ce1-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="67ce1-107">値<xref:System.Drawing.StringFormatFlags.DirectionVertical>のメンバーである、<xref:System.Drawing.StringFormatFlags>列挙します。</span><span class="sxs-lookup"><span data-stu-id="67ce1-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="67ce1-108">次の図は、垂直方向のテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="67ce1-108">The following illustration shows the vertical text.</span></span>  
  
 <span data-ttu-id="67ce1-109">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span><span class="sxs-lookup"><span data-stu-id="67ce1-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext5.png "csfontstext5")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="67ce1-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="67ce1-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="67ce1-111">前の例は Windows フォームで使用するために設計され、必要があります<xref:System.Windows.Forms.PaintEventArgs> `e` 、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="67ce1-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ce1-112">参照</span><span class="sxs-lookup"><span data-stu-id="67ce1-112">See Also</span></span>  
 [<span data-ttu-id="67ce1-113">方法: GDI を使用してテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="67ce1-113">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
