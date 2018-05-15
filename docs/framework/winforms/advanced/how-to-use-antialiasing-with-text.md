---
title: '方法: テキストでのアンチエイリアシングの使用'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 842c1fb0b73533fd2e87474b9e8cfa282eba2a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="5f8fb-102">方法: テキストでのアンチエイリアシングの使用</span><span class="sxs-lookup"><span data-stu-id="5f8fb-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="5f8fb-103">*アンチエイリアシング*描画されたグラフィックスとテキストの外観または読みやすさを向上させるにギザギザした境界のスムージングを指します。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="5f8fb-104">マネージで[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]クラス、低品質テキストだけでなく、高画質のアンチ エイリアス化テキストを描画できます。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="5f8fb-105">通常、高品質のレンダリングより低い品質レンダリング処理時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="5f8fb-106">テキスト品質レベルを設定するには、設定、<xref:System.Drawing.Graphics.TextRenderingHint%2A>のプロパティ、<xref:System.Drawing.Graphics>の要素のいずれかに、<xref:System.Drawing.Text.TextRenderingHint>列挙型</span><span class="sxs-lookup"><span data-stu-id="5f8fb-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f8fb-107">例</span><span class="sxs-lookup"><span data-stu-id="5f8fb-107">Example</span></span>  
 <span data-ttu-id="5f8fb-108">次のコード例では、2 つの異なる品質設定でテキストを描画します。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="5f8fb-109">次の図は、コード例の出力を示します。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="5f8fb-110">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="5f8fb-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f8fb-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5f8fb-111">Compiling the Code</span></span>  
 <span data-ttu-id="5f8fb-112">前のコード例は、Windows フォームで使用するために設計されていて、必要な<xref:System.Windows.Forms.PaintEventArgs> `e`、パラメーターのある<xref:System.Windows.Forms.PaintEventHandler>です。</span><span class="sxs-lookup"><span data-stu-id="5f8fb-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8fb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f8fb-113">See Also</span></span>  
 [<span data-ttu-id="5f8fb-114">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="5f8fb-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
