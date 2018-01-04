---
title: "方法 : StreamGeometry を使用して図形を作成する"
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
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a333fd6c1906eaea2c8eaf2c3b07502b5a9c4d40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="a3757-102">方法 : StreamGeometry を使用して図形を作成する</span><span class="sxs-lookup"><span data-stu-id="a3757-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="a3757-103"><xref:System.Windows.Media.StreamGeometry>軽量な代替手段は、<xref:System.Windows.Media.PathGeometry>幾何学図形を作成するためです。</span><span class="sxs-lookup"><span data-stu-id="a3757-103"><xref:System.Windows.Media.StreamGeometry> is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="a3757-104">使用して、<xref:System.Windows.Media.StreamGeometry>複合ジオメトリを記述する必要がある場合は、サポートするオーバーヘッドのデータ バインディング、アニメーション、または変更しません。</span><span class="sxs-lookup"><span data-stu-id="a3757-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="a3757-105">などにより、効率、<xref:System.Windows.Media.StreamGeometry>クラスは、装飾を記述するための適切な選択です。</span><span class="sxs-lookup"><span data-stu-id="a3757-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3757-106">例</span><span class="sxs-lookup"><span data-stu-id="a3757-106">Example</span></span>  
 <span data-ttu-id="a3757-107">次の例では、属性の構文を使用して、作成、三角形<xref:System.Windows.Media.StreamGeometry>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a3757-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="a3757-108">詳細については<xref:System.Windows.Media.StreamGeometry>属性構文を参照してください、[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)ページ。</span><span class="sxs-lookup"><span data-stu-id="a3757-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3757-109">例</span><span class="sxs-lookup"><span data-stu-id="a3757-109">Example</span></span>  
 <span data-ttu-id="a3757-110">次の例では、<xref:System.Windows.Media.StreamGeometry>をコード内の三角形を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3757-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="a3757-111">最初に、例、<xref:System.Windows.Media.StreamGeometry>を取得し、<xref:System.Windows.Media.StreamGeometryContext>三角形の説明を使用しています。</span><span class="sxs-lookup"><span data-stu-id="a3757-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="a3757-112">例</span><span class="sxs-lookup"><span data-stu-id="a3757-112">Example</span></span>  
 <span data-ttu-id="a3757-113">次の例は、使用するメソッドを作成、<xref:System.Windows.Media.StreamGeometry>と<xref:System.Windows.Media.StreamGeometryContext>を指定したパラメーターに基づいて幾何学図形を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3757-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a3757-114">参照</span><span class="sxs-lookup"><span data-stu-id="a3757-114">See Also</span></span>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [<span data-ttu-id="a3757-115">PathGeometry を使用して図形を作成する</span><span class="sxs-lookup"><span data-stu-id="a3757-115">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [<span data-ttu-id="a3757-116">ジオメトリの概要</span><span class="sxs-lookup"><span data-stu-id="a3757-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
