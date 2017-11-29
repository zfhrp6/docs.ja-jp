---
title: "方法 : オブジェクトに複数の変換を適用する"
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
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 954d29664da10f38ffd5cc97faf24343b50f1b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a><span data-ttu-id="5b3dd-102">方法 : オブジェクトに複数の変換を適用する</span><span class="sxs-lookup"><span data-stu-id="5b3dd-102">How to: Apply Multiple Transforms to an Object</span></span>
<span data-ttu-id="5b3dd-103">この例を使用する方法を示しています、 <xref:System.Windows.Media.TransformGroup> 2 つ以上のグループに<xref:System.Windows.Media.Transform>に 1 つの複合オブジェクト<xref:System.Windows.Media.Transform>です。</span><span class="sxs-lookup"><span data-stu-id="5b3dd-103">This example shows how to use a <xref:System.Windows.Media.TransformGroup> to group two or more <xref:System.Windows.Media.Transform> objects into a single composite <xref:System.Windows.Media.Transform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b3dd-104">例</span><span class="sxs-lookup"><span data-stu-id="5b3dd-104">Example</span></span>  
 <span data-ttu-id="5b3dd-105">次の例では、<xref:System.Windows.Media.TransformGroup>を適用する、<xref:System.Windows.Media.ScaleTransform>と<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.Controls.Button>です。</span><span class="sxs-lookup"><span data-stu-id="5b3dd-105">The following example uses a <xref:System.Windows.Media.TransformGroup> to apply a <xref:System.Windows.Media.ScaleTransform> and a <xref:System.Windows.Media.RotateTransform> to a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5b3dd-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b3dd-106">See Also</span></span>  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Media.TransformGroup>  
 [<span data-ttu-id="5b3dd-107">変換の概要</span><span class="sxs-lookup"><span data-stu-id="5b3dd-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="5b3dd-108">2-D 変換のサンプル</span><span class="sxs-lookup"><span data-stu-id="5b3dd-108">2-D Transforms Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=158252)
