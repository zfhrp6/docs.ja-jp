---
title: "方法 : ビジュアル内のジオメトリのヒット テストを実行する"
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
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab125fe4031b5408eb202f21ce0fdf4314781f1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="177db-102">方法 : ビジュアル内のジオメトリのヒット テストを実行する</span><span class="sxs-lookup"><span data-stu-id="177db-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="177db-103">この例は、1 つまたは複数を構成している visual オブジェクトに対してヒット テストを実行する方法を示しています。<xref:System.Windows.Media.Geometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="177db-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="177db-104">例</span><span class="sxs-lookup"><span data-stu-id="177db-104">Example</span></span>  
 <span data-ttu-id="177db-105">次の例は、取得する方法を示します、<xref:System.Windows.Media.DrawingGroup>を使用する visual オブジェクトから、<xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="177db-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="177db-106">描画されるコンテンツ内の各図面のヒット テストが実行されます、<xref:System.Windows.Media.DrawingGroup>をどのジオメトリにヒットしたかを判断します。</span><span class="sxs-lookup"><span data-stu-id="177db-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177db-107">ほとんどの場合でを使って、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>点と交差するビジュアルの描画された内容にするかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="177db-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="177db-108"><xref:System.Windows.Media.Geometry.FillContains%2A>メソッドはオーバー ロードされたメソッドを使用して、指定したヒット テストするを<xref:System.Windows.Point>または<xref:System.Windows.Media.Geometry>です。</span><span class="sxs-lookup"><span data-stu-id="177db-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="177db-109">ジオメトリに線が付いている場合は、塗りつぶしの境界の外側までストロークを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="177db-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="177db-110">この場合を呼び出したい場合があります<xref:System.Windows.Media.Geometry.StrokeContains%2A>に加えて<xref:System.Windows.Media.Geometry.FillContains%2A>です。</span><span class="sxs-lookup"><span data-stu-id="177db-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="177db-111">提供することも、<xref:System.Windows.Media.ToleranceType>ベジエのフラット化のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="177db-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="177db-112">このサンプルでは、ジオメトリに適用される可能性のある変換やクリッピングは考慮していません。</span><span class="sxs-lookup"><span data-stu-id="177db-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="177db-113">また、スタイルが設定されたコントロールには直接関連付けられた描画がないので、このサンプルはスタイルが設定されたコントロールに対しては機能しません。</span><span class="sxs-lookup"><span data-stu-id="177db-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="177db-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="177db-114">See Also</span></span>  
 [<span data-ttu-id="177db-115">ビジュアル層でのヒット テスト</span><span class="sxs-lookup"><span data-stu-id="177db-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="177db-116">パラメーターとしてジオメトリを使用してヒット テストを実行する</span><span class="sxs-lookup"><span data-stu-id="177db-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
