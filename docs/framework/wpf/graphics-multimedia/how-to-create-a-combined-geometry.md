---
title: '方法 : 結合したジオメトリを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: 107e0342b822633ccb4f51f256c121cc80c297f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561122"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="34d85-102">方法 : 結合したジオメトリを作成する</span><span class="sxs-lookup"><span data-stu-id="34d85-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="34d85-103">この例では、ジオメトリを結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="34d85-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="34d85-104">2 つのジオメトリを組み合わせるを使用して、<xref:System.Windows.Media.CombinedGeometry>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="34d85-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="34d85-105">設定の<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>結合、および設定を 2 つのジオメトリを持つプロパティ、<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A>ジオメトリを一緒に結合される方法を決定するプロパティを`Union`、 `Intersect`、 `Exclude`、または`Xor`.</span><span class="sxs-lookup"><span data-stu-id="34d85-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="34d85-106">2 つ以上のジオメトリから複合ジオメトリを作成するには、使用、<xref:System.Windows.Media.GeometryGroup>です。</span><span class="sxs-lookup"><span data-stu-id="34d85-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d85-107">例</span><span class="sxs-lookup"><span data-stu-id="34d85-107">Example</span></span>  
 <span data-ttu-id="34d85-108">次の例で、<xref:System.Windows.Media.CombinedGeometry>の geometry 組み合わせモードで定義された`Exclude`です。</span><span class="sxs-lookup"><span data-stu-id="34d85-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="34d85-109">両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 センター オフセットを含むが、同じの半径の円として定義されます。</span><span class="sxs-lookup"><span data-stu-id="34d85-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="34d85-110">![組み合わせモードの結果、除外の](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="34d85-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="34d85-111">結合したジオメトリの除外</span><span class="sxs-lookup"><span data-stu-id="34d85-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="34d85-112">次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の組み合わせモードで定義された`Intersect`です。</span><span class="sxs-lookup"><span data-stu-id="34d85-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="34d85-113">両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 センター オフセットを含むが、同じの半径の円として定義されます。</span><span class="sxs-lookup"><span data-stu-id="34d85-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="34d85-114">![組み合わせモードの交差部分の結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="34d85-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="34d85-115">結合された Geometry を交差します。</span><span class="sxs-lookup"><span data-stu-id="34d85-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="34d85-116">次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の組み合わせモードで定義された`Union`です。</span><span class="sxs-lookup"><span data-stu-id="34d85-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="34d85-117">両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 センター オフセットを含むが、同じの半径の円として定義されます。</span><span class="sxs-lookup"><span data-stu-id="34d85-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="34d85-118">![和集合結合モードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="34d85-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="34d85-119">結合された Geometry の和集合</span><span class="sxs-lookup"><span data-stu-id="34d85-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="34d85-120">次のマークアップで、<xref:System.Windows.Media.CombinedGeometry>の組み合わせモードで定義された`Xor`です。</span><span class="sxs-lookup"><span data-stu-id="34d85-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="34d85-121">両方<xref:System.Windows.Media.CombinedGeometry.Geometry1%2A>と<xref:System.Windows.Media.CombinedGeometry.Geometry2%2A>50 センター オフセットを含むが、同じの半径の円として定義されます。</span><span class="sxs-lookup"><span data-stu-id="34d85-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="34d85-122">![Xor 結合モードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="34d85-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="34d85-123">結合したジオメトリ Xor</span><span class="sxs-lookup"><span data-stu-id="34d85-123">Combined Geometry Xor</span></span>
