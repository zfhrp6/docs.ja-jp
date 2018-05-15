---
title: '方法 : Point4D 構造体が等価かどうかをテストする'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: 1ec844c8fb0aceaaec6030c2e9d5cb30cf984f43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="2129a-102">方法 : Point4D 構造体が等価かどうかをテストする</span><span class="sxs-lookup"><span data-stu-id="2129a-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="2129a-103">この例をテストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>等値演算子および非等値の構造体。</span><span class="sxs-lookup"><span data-stu-id="2129a-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="2129a-104">次のコードをテストする方法を示しています。<xref:System.Windows.Media.Media3D.Point4D>構造の等値演算子および非等値を使用して、<xref:System.Windows.Media.Media3D.Point4D>等しいかどうかの方法です。</span><span class="sxs-lookup"><span data-stu-id="2129a-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="2129a-105"><xref:System.Windows.Media.Media3D.Point4D>構造があるオーバー ロードされた等しいかどうかを使用する等値テスト (`==`) 演算子をオーバー ロードされた非等値を使用して非等値を (`!=`) 演算子、および最後に、<xref:System.Windows.Media.Media3D.Point3D>構造と<xref:System.Windows.Media.Media3D.Point4D>使用して、静的等値の構造がチェックされます<xref:System.Windows.Media.Media3D.Point4D.Equals%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2129a-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2129a-106">例</span><span class="sxs-lookup"><span data-stu-id="2129a-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="2129a-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="2129a-107">See Also</span></span>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
