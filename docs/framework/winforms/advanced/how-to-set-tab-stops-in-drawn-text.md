---
title: '方法 : 描画されたテキストにタブ ストップを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: e7f3fe9757db26bcc9dc9735f3d3d854edb7c099
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523638"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="98231-102">方法 : 描画されたテキストにタブ ストップを設定する</span><span class="sxs-lookup"><span data-stu-id="98231-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="98231-103">テキストのタブ ストップを設定するには呼び出すことによって、<xref:System.Drawing.StringFormat.SetTabStops%2A>のメソッド、<xref:System.Drawing.StringFormat>オブジェクトを渡す、<xref:System.Drawing.StringFormat>オブジェクトを<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="98231-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98231-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>を使用して既存のタブを展開することができますが、描画するテキストへのタブ位置を追加するサポートされていませんが停止する機能は、<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>フラグ。</span><span class="sxs-lookup"><span data-stu-id="98231-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98231-105">例</span><span class="sxs-lookup"><span data-stu-id="98231-105">Example</span></span>  
 <span data-ttu-id="98231-106">次の例では、150、250、および 350 にタブ ストップを設定します。</span><span class="sxs-lookup"><span data-stu-id="98231-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="98231-107">次に、コードでは、名前と試験の点数のタブ付きの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98231-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="98231-108">次の図は、タブ付きのテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="98231-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="98231-109">![フォント テキスト](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="98231-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="98231-110">次のコードは 2 つの引数を渡す、<xref:System.Drawing.StringFormat.SetTabStops%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="98231-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="98231-111">2 番目の引数は、タブのオフセットを含む配列です。</span><span class="sxs-lookup"><span data-stu-id="98231-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="98231-112">渡される最初の引数<xref:System.Drawing.StringFormat.SetTabStops%2A>が 0 で、配列内の最初のオフセットが 0、外接する四角形の左端の位置から測定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="98231-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98231-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="98231-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="98231-114">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="98231-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98231-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="98231-115">See Also</span></span>  
 [<span data-ttu-id="98231-116">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="98231-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="98231-117">方法: GDI を使用してテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="98231-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
