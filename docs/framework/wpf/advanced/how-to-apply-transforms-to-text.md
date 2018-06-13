---
title: '方法 : テキストに変換を適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: 531537013ab3bbfba278ca63e14155341eefc826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544923"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="0703a-102">方法 : テキストに変換を適用する</span><span class="sxs-lookup"><span data-stu-id="0703a-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="0703a-103">変換を利用すると、アプリケーションのテキストの表示を変えることができます。</span><span class="sxs-lookup"><span data-stu-id="0703a-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="0703a-104">次の例は、内のテキストの表示には影響を描画変換のさまざまな種類を使用して、<xref:System.Windows.Controls.TextBlock>コントロール。</span><span class="sxs-lookup"><span data-stu-id="0703a-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0703a-105">例</span><span class="sxs-lookup"><span data-stu-id="0703a-105">Example</span></span>  
 <span data-ttu-id="0703a-106">次は、x と y の 2 次元平面に指定した点を中心にテキストを回転させた例です。</span><span class="sxs-lookup"><span data-stu-id="0703a-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="0703a-107">![RotateTransform を使用して回転したテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="0703a-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="0703a-108">90 度回転させたテキストの例</span><span class="sxs-lookup"><span data-stu-id="0703a-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="0703a-109">次のコード例では、<xref:System.Windows.Media.RotateTransform>テキストを回転させる。</span><span class="sxs-lookup"><span data-stu-id="0703a-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="0703a-110"><xref:System.Windows.Media.RotateTransform.Angle%2A> 90 の値が、要素を時計回りに 90 度回転させます。</span><span class="sxs-lookup"><span data-stu-id="0703a-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="0703a-111">テキストの 2 行目を x 軸に沿って 150% 拡大し、3 行目を y 軸に沿って 150% 拡大した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0703a-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="0703a-112">![ScaleTransform を使用してスケールされたテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="0703a-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="0703a-113">拡大縮小されたテキストの例</span><span class="sxs-lookup"><span data-stu-id="0703a-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="0703a-114">次のコード例では、<xref:System.Windows.Media.ScaleTransform>スケール テキスト、元のサイズからにします。</span><span class="sxs-lookup"><span data-stu-id="0703a-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="0703a-115">テキストの拡大縮小は、テキストのフォント サイズを増やすことと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="0703a-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="0703a-116">フォント サイズは、サイズを変えても最良の解像度が得られるように、互いに依存せずに計算されます。</span><span class="sxs-lookup"><span data-stu-id="0703a-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="0703a-117">一方で、テキストの拡大縮小では、元のサイズのテキストの比率が維持されます。</span><span class="sxs-lookup"><span data-stu-id="0703a-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="0703a-118">x 軸に沿って傾斜させたテキストの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0703a-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="0703a-119">![SkewTransform を使用して傾斜させたテキスト](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="0703a-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="0703a-120">傾斜させたテキストの例</span><span class="sxs-lookup"><span data-stu-id="0703a-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="0703a-121">次のコード例では、<xref:System.Windows.Media.SkewTransform>傾けるにはテキストです。</span><span class="sxs-lookup"><span data-stu-id="0703a-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="0703a-122">傾斜はスキューと呼ばれることもありますが、一様でない方法で座標空間を拡大する変換です。</span><span class="sxs-lookup"><span data-stu-id="0703a-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="0703a-123">この例では、2 つのテキスト文字列が x 座標に沿って -30° と 30° とに傾斜します。</span><span class="sxs-lookup"><span data-stu-id="0703a-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="0703a-124">次の例では、x 軸と y 軸に沿ってテキストが変換または移動されます。</span><span class="sxs-lookup"><span data-stu-id="0703a-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="0703a-125">![TranslateTransform を使用してオフセット テキスト](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="0703a-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="0703a-126">変換されたテキストの例</span><span class="sxs-lookup"><span data-stu-id="0703a-126">Example of translated text</span></span>  
  
 <span data-ttu-id="0703a-127">次のコード例では、<xref:System.Windows.Media.TranslateTransform>テキストのオフセット。</span><span class="sxs-lookup"><span data-stu-id="0703a-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="0703a-128">この例では、メインのテキストの下にわずかに中心をずらしたコピーが付き、影のような効果を作っています。</span><span class="sxs-lookup"><span data-stu-id="0703a-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="0703a-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect>シャドウ効果を提供する豊富な一連の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0703a-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="0703a-130">詳細については、次を参照してください。[影付きのテキストの作成](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md)です。</span><span class="sxs-lookup"><span data-stu-id="0703a-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0703a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0703a-131">See Also</span></span>  
 [<span data-ttu-id="0703a-132">アニメーションをテキストに適用する</span><span class="sxs-lookup"><span data-stu-id="0703a-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
