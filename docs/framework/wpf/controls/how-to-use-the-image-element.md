---
title: "方法 : イメージ要素を使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26beb6b0f5c446bbddd293e76ae79d062aa0fe48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-image-element"></a><span data-ttu-id="804bc-102">方法 : イメージ要素を使用する</span><span class="sxs-lookup"><span data-stu-id="804bc-102">How to: Use the Image Element</span></span>
<span data-ttu-id="804bc-103">この例を使用して、アプリケーションでイメージを含める方法を示しています、<xref:System.Windows.Controls.Image>要素。</span><span class="sxs-lookup"><span data-stu-id="804bc-103">This example shows how to include images in an application by using the <xref:System.Windows.Controls.Image> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="804bc-104">例</span><span class="sxs-lookup"><span data-stu-id="804bc-104">Example</span></span>  
 <span data-ttu-id="804bc-105">次の例では、幅 200 ピクセルのイメージをレンダリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="804bc-105">The following example shows how to render an image 200 pixels wide.</span></span> <span data-ttu-id="804bc-106">この[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例では、イメージの定義に属性の構文とプロパティ タグ構文の両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="804bc-106">In this [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example, both attribute syntax and property tag syntax are used to define the image.</span></span> <span data-ttu-id="804bc-107">属性構文とプロパティ構文の詳細については、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="804bc-107">For more information on attribute syntax and property syntax, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span> <span data-ttu-id="804bc-108">A<xref:System.Windows.Media.Imaging.BitmapImage>画像のソース データを定義するために使用して、タグ構文の例でプロパティを明示的に定義されています。</span><span class="sxs-lookup"><span data-stu-id="804bc-108">A <xref:System.Windows.Media.Imaging.BitmapImage> is used to define the image's source data and is explicitly defined for the property tag syntax example.</span></span> <span data-ttu-id="804bc-109">さらに、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>の<xref:System.Windows.Media.Imaging.BitmapImage>と同じ幅に設定されている、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Controls.Image>です。</span><span class="sxs-lookup"><span data-stu-id="804bc-109">In addition, the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> of the <xref:System.Windows.Media.Imaging.BitmapImage> is set to the same width as the <xref:System.Windows.FrameworkElement.Width%2A> of the <xref:System.Windows.Controls.Image>.</span></span> <span data-ttu-id="804bc-110">これは、イメージのレンダリングに使用するメモリ量が最小になるように実行されます。</span><span class="sxs-lookup"><span data-stu-id="804bc-110">This is done to ensure that the minimum amount of memory is used rendering the image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804bc-111">一般に、表示の画像のサイズを指定する場合のみを指定、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>が、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="804bc-111">In general, if you want to specify the size of a rendered image, specify only the <xref:System.Windows.FrameworkElement.Width%2A> or the <xref:System.Windows.FrameworkElement.Height%2A> but not both.</span></span> <span data-ttu-id="804bc-112">いずれかのみを指定する場合、イメージの縦横比が保持されます。</span><span class="sxs-lookup"><span data-stu-id="804bc-112">If you only specify one, the image's aspect ratio is preserved.</span></span> <span data-ttu-id="804bc-113">それ以外の場合、イメージの拡大表示やゆがみ表示が予期せず発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="804bc-113">Otherwise, the image may unexpectedly appear stretched or warped.</span></span> <span data-ttu-id="804bc-114">イメージを制御するの動作の拡張を使用して、<xref:System.Windows.Controls.Image.Stretch%2A>と<xref:System.Windows.Controls.Image.StretchDirection%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="804bc-114">To control the image's stretching behavior, use the <xref:System.Windows.Controls.Image.Stretch%2A> and <xref:System.Windows.Controls.Image.StretchDirection%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804bc-115">いずれかで イメージのサイズを指定する<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>、いずれかを設定することも必要があります<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>または<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A>それぞれ同じサイズにします。</span><span class="sxs-lookup"><span data-stu-id="804bc-115">When you specify the size of an image with either <xref:System.Windows.FrameworkElement.Width%2A> or <xref:System.Windows.FrameworkElement.Height%2A>, you should also set either <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> or <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A> to the same respective size.</span></span>  
  
 <span data-ttu-id="804bc-116"><xref:System.Windows.Controls.Image.Stretch%2A>プロパティでは、イメージ要素の塗りつぶしを画像のソースを拡大する方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="804bc-116">The <xref:System.Windows.Controls.Image.Stretch%2A> property determines how the image source is stretched to fill the image element.</span></span> <span data-ttu-id="804bc-117">詳細については、<xref:System.Windows.Media.Stretch> 列挙型のページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="804bc-117">For more information, see the <xref:System.Windows.Media.Stretch> enumeration.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="804bc-118">例</span><span class="sxs-lookup"><span data-stu-id="804bc-118">Example</span></span>  
 <span data-ttu-id="804bc-119">次の例は、コードを使用して幅 200 ピクセルのイメージをレンダリングする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="804bc-119">The following example shows how to render an image 200 pixels wide using code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="804bc-120">設定<xref:System.Windows.Media.Imaging.BitmapImage>プロパティ内で実行する必要があります、<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>と<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>ブロックします。</span><span class="sxs-lookup"><span data-stu-id="804bc-120">Setting <xref:System.Windows.Media.Imaging.BitmapImage> properties must be done within a <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> and <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> block.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="804bc-121">参照</span><span class="sxs-lookup"><span data-stu-id="804bc-121">See Also</span></span>  
 [<span data-ttu-id="804bc-122">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="804bc-122">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
