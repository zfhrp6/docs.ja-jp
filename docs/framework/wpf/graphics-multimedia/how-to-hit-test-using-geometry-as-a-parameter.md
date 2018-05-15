---
title: '方法 : パラメーターとしてジオメトリを使用してヒット テストを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 57b04f7f8c9bcc21f6b970c2981c2bab51044c10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="45e24-102">方法 : パラメーターとしてジオメトリを使用してヒット テストを実行する</span><span class="sxs-lookup"><span data-stu-id="45e24-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="45e24-103">この例を使用してビジュアル オブジェクトに対してヒット テストを実行する方法を示しています、<xref:System.Windows.Media.Geometry>ヒットとしてパラメーターをテストします。</span><span class="sxs-lookup"><span data-stu-id="45e24-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45e24-104">例</span><span class="sxs-lookup"><span data-stu-id="45e24-104">Example</span></span>  
 <span data-ttu-id="45e24-105">次の例を使用して、ヒット テストを設定する方法を示しています。<xref:System.Windows.Media.GeometryHitTestParameters>の、<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="45e24-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="45e24-106"><xref:System.Windows.Point>に渡される値、`OnMouseDown`メソッドの使用を作成、<xref:System.Windows.Media.Geometry>ヒット テストの範囲を拡張するためにオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="45e24-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="45e24-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>プロパティ<xref:System.Windows.Media.GeometryHitTestResult>を使用するヒット テストの結果に関する情報を提供、<xref:System.Windows.Media.Geometry>ヒットとしてパラメーターをテストします。</span><span class="sxs-lookup"><span data-stu-id="45e24-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="45e24-108">ヒット テストのジオメトリ (青い円) と対象のビジュアル オブジェクト (赤い正方形) の描画されるコンテンツとの関係を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="45e24-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="45e24-109">![ヒット テストで使用される IntersectionDetail のダイアグラム](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="45e24-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="45e24-110">ヒット テストのジオメトリと対象のビジュアル オブジェクトの交差部分</span><span class="sxs-lookup"><span data-stu-id="45e24-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="45e24-111">次の例は、ヒット テストのコールバックを実装する方法を示しています。 ときに、<xref:System.Windows.Media.Geometry>ヒット テスト パラメーターとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="45e24-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="45e24-112">`result`にパラメーターをキャスト、<xref:System.Windows.Media.GeometryHitTestResult>の値を取得するために、<xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="45e24-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="45e24-113">プロパティの値を使用すると、かどうかを<xref:System.Windows.Media.Geometry>ヒット テスト パラメーターの完全または部分的に含まれるヒット テスト対象の描画された内容。</span><span class="sxs-lookup"><span data-stu-id="45e24-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="45e24-114">ここに示すサンプル コードでは、完全に対象の境界内に含まれるビジュアルについてのみ、ヒット テストの結果をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="45e24-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="45e24-115"><xref:System.Windows.Media.HitTestResult>交差部分の詳細はときに、コールバックを呼び出すことはできません<xref:System.Windows.Media.IntersectionDetail.Empty>です。</span><span class="sxs-lookup"><span data-stu-id="45e24-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e24-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="45e24-116">See Also</span></span>  
 [<span data-ttu-id="45e24-117">ビジュアル層でのヒット テスト</span><span class="sxs-lookup"><span data-stu-id="45e24-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="45e24-118">ビジュアル内のジオメトリのヒット テストを実行する</span><span class="sxs-lookup"><span data-stu-id="45e24-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
