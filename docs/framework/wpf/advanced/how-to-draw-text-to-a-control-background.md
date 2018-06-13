---
title: '方法: コントロールの背景にテキストを描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], drawing text to backgrounds
- text [WPF], drawing to control backgrounds
- drawing [WPF], text to control backgrounds
- backgrounds [WPF], drawing text to
- typography [WPF], drawing text to control backgrounds
ms.assetid: 686d8fba-f61c-4974-a871-c635d67a7f69
ms.openlocfilehash: f79ec4f2c394fdc9462f4fd00942673b4536d713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542978"
---
# <a name="how-to-draw-text-to-a-control39s-background"></a><span data-ttu-id="f91f1-102">方法: コントロールの背景にテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="f91f1-102">How to: Draw Text to a Control&#39;s Background</span></span>
<span data-ttu-id="f91f1-103">コントロールの背景に直接テキストを描画するにはテキスト文字列を変換することで、<xref:System.Windows.Media.FormattedText>オブジェクト、およびコントロールのオブジェクトを描画<xref:System.Windows.Media.DrawingContext>です。</span><span class="sxs-lookup"><span data-stu-id="f91f1-103">You can draw text directly to the background of a control by converting a text string to a <xref:System.Windows.Media.FormattedText> object, and then drawing the object to the control's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="f91f1-104">派生したオブジェクトの背景に描画用に、この手法を使用することもできます<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.Canvas>と<xref:System.Windows.Controls.StackPanel>です。</span><span class="sxs-lookup"><span data-stu-id="f91f1-104">You can also use this technique for drawing to the background of objects derived from <xref:System.Windows.Controls.Panel>, such as <xref:System.Windows.Controls.Canvas> and <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
 <span data-ttu-id="f91f1-105">![背景としてテキストを表示するコントロール](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span><span class="sxs-lookup"><span data-stu-id="f91f1-105">![Controls displaying text as background](../../../../docs/framework/wpf/advanced/media/drawtext2background01.png "DrawText2Background01")</span></span>  
<span data-ttu-id="f91f1-106">カスタム テキスト背景のコントロールの例</span><span class="sxs-lookup"><span data-stu-id="f91f1-106">Example of controls with custom text backgrounds</span></span>  
  
## <a name="example"></a><span data-ttu-id="f91f1-107">例</span><span class="sxs-lookup"><span data-stu-id="f91f1-107">Example</span></span>  
 <span data-ttu-id="f91f1-108">コントロールの背景を描画するには、新規作成<xref:System.Windows.Media.DrawingBrush>オブジェクトおよびオブジェクトの変換後のテキストを描画<xref:System.Windows.Media.DrawingContext>です。</span><span class="sxs-lookup"><span data-stu-id="f91f1-108">To draw to the background of a control, create a new <xref:System.Windows.Media.DrawingBrush> object and draw the converted text to the object's <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="f91f1-109">その後、新しい割り当てる<xref:System.Windows.Media.DrawingBrush>コントロールの背景のプロパティにします。</span><span class="sxs-lookup"><span data-stu-id="f91f1-109">Then, assign the new <xref:System.Windows.Media.DrawingBrush> to the control's background property.</span></span>  
  
 <span data-ttu-id="f91f1-110">次のコード例を作成する方法を示しています、<xref:System.Windows.Media.FormattedText>オブジェクトし、の背景を描画する<xref:System.Windows.Controls.Label>と<xref:System.Windows.Controls.Button>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f91f1-110">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and draw to the background of a <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.Button> object.</span></span>  
  
 [!code-csharp[DrawTextToControlBackground#DrawTextToControlBackground1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawTextToControlBackground/CSHARP/Window1.xaml.cs#drawtexttocontrolbackground1)]  
  
## <a name="see-also"></a><span data-ttu-id="f91f1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f91f1-111">See Also</span></span>  
 <xref:System.Windows.Media.FormattedText>  
 [<span data-ttu-id="f91f1-112">書式設定されたテキストの描画</span><span class="sxs-lookup"><span data-stu-id="f91f1-112">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
