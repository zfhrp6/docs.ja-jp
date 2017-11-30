---
title: "方法 : MatrixTransform を使用してカスタム変換を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4995c5d712807e91b27c7afacd6f5b7015cb5898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="0ff61-102">方法 : MatrixTransform を使用してカスタム変換を作成する</span><span class="sxs-lookup"><span data-stu-id="0ff61-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="0ff61-103">この例を使用する方法を示しています、<xref:System.Windows.Media.MatrixTransform>変換 (移動)、位置、stretch、およびの傾斜、<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="0ff61-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ff61-104">使用して、<xref:System.Windows.Media.MatrixTransform>では提供されないカスタム変換を作成するクラス、 <xref:System.Windows.Media.RotateTransform>、 <xref:System.Windows.Media.SkewTransform>、 <xref:System.Windows.Media.ScaleTransform>、または<xref:System.Windows.Media.TranslateTransform>クラスです。</span><span class="sxs-lookup"><span data-stu-id="0ff61-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff61-105">例</span><span class="sxs-lookup"><span data-stu-id="0ff61-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="0ff61-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ff61-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="0ff61-107">変換の概要</span><span class="sxs-lookup"><span data-stu-id="0ff61-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="0ff61-108">方法トピック</span><span class="sxs-lookup"><span data-stu-id="0ff61-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="0ff61-109">WPF での図形と基本描画の概要</span><span class="sxs-lookup"><span data-stu-id="0ff61-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
