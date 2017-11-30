---
title: "方法 : 反射を作成する"
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
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3032f46843c6d8efc53c45a927feae7068c3eb5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="0c9eb-102">方法 : 反射を作成する</span><span class="sxs-lookup"><span data-stu-id="0c9eb-102">How to: Create a Reflection</span></span>
<span data-ttu-id="0c9eb-103">この例を使用する方法を示しています、<xref:System.Windows.Media.VisualBrush>反射を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c9eb-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="0c9eb-104"><xref:System.Windows.Media.VisualBrush>既存 visual を表示することができます、反射や拡大などの興味深いビジュアル効果を生成するためにこの機能を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0c9eb-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c9eb-105">例</span><span class="sxs-lookup"><span data-stu-id="0c9eb-105">Example</span></span>  
 <span data-ttu-id="0c9eb-106">次の例では、<xref:System.Windows.Media.VisualBrush>の反射、<xref:System.Windows.Controls.Border>いくつかの要素を格納しています。</span><span class="sxs-lookup"><span data-stu-id="0c9eb-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="0c9eb-107">次の図は、この例で生成される出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="0c9eb-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="0c9eb-108">![A ビジュアル オブジェクトの反映](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="0c9eb-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="0c9eb-109">反映された Visual オブジェクト</span><span class="sxs-lookup"><span data-stu-id="0c9eb-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="0c9eb-110">反射を作成する方法と、画面の部分を拡大する方法を示す例が含まれている完全なサンプルは、次を参照してください。 [VisualBrush サンプル](http://go.microsoft.com/fwlink/?LinkID=160049)です。</span><span class="sxs-lookup"><span data-stu-id="0c9eb-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9eb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c9eb-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="0c9eb-112">イメージ、描画、およびビジュアルによる塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="0c9eb-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
