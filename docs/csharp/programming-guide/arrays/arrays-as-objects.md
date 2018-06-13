---
title: オブジェクトとしての配列 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 07e824d21ffc02ba7a3c33507d22d1dc7a1ac638
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33312609"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="37798-102">オブジェクトとしての配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="37798-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="37798-103">C# の配列は、実際はオブジェクトです。C や C++ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。</span><span class="sxs-lookup"><span data-stu-id="37798-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="37798-104"><xref:System.Array> はすべての配列型の抽象基本データ型で、</span><span class="sxs-lookup"><span data-stu-id="37798-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="37798-105"><xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="37798-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="37798-106">この例としては、<xref:System.Array.Length%2A> プロパティを使用して、配列の長さを取得する場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="37798-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="37798-107">`numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="37798-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="37798-108"><xref:System.Array> クラスには、配列の並べ替え、検索、コピーを行うための便利なメソッドやプロパティが他にも多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="37798-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37798-109">例</span><span class="sxs-lookup"><span data-stu-id="37798-109">Example</span></span>  
 <span data-ttu-id="37798-110">次の例では、<xref:System.Array.Rank%2A> プロパティを使用して、配列の次元数を表示します。</span><span class="sxs-lookup"><span data-stu-id="37798-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="37798-111">参照</span><span class="sxs-lookup"><span data-stu-id="37798-111">See Also</span></span>  
 [<span data-ttu-id="37798-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="37798-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="37798-113">配列</span><span class="sxs-lookup"><span data-stu-id="37798-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="37798-114">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="37798-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="37798-115">多次元配列</span><span class="sxs-lookup"><span data-stu-id="37798-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="37798-116">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="37798-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
