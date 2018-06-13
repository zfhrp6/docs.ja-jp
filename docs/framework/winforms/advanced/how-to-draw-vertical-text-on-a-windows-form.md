---
title: '方法 : Windows フォームに縦書きテキストを描画する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
ms.openlocfilehash: afd09a41c46049c5a963558a709b00864fa6180f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521542"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="36466-102">方法 : Windows フォームに縦書きテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="36466-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="36466-103">次のコード例を使用して、フォームに縦書きテキストを描画する方法を示しています、<xref:System.Drawing.Graphics.DrawString%2A>メソッドの<xref:System.Drawing.Graphics>します。</span><span class="sxs-lookup"><span data-stu-id="36466-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36466-104">例</span><span class="sxs-lookup"><span data-stu-id="36466-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="36466-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="36466-105">Compiling the Code</span></span>  
 <span data-ttu-id="36466-106">このメソッドを呼び出すことはできません、<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="36466-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="36466-107">フォームがサイズ変更されるか、別の形式によって隠されている場合、描画済みのコンテンツを再描画されませんされます。</span><span class="sxs-lookup"><span data-stu-id="36466-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="36466-108">コンテンツを自動的に再描画するために、オーバーライドする必要があります、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="36466-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="36466-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="36466-109">Robust Programming</span></span>  
 <span data-ttu-id="36466-110">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36466-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="36466-111">Arial フォントがインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="36466-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36466-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="36466-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="36466-113">グラフィックス プログラミングについて</span><span class="sxs-lookup"><span data-stu-id="36466-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="36466-114">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="36466-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
