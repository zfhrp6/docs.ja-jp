---
title: '方法: 参照の等価性 (同値) をテストする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 78a6bf1f5d4a93bd561faada91b4a11f52692dbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="1eee3-102">方法: 参照の等価性 (同値) をテストする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1eee3-102">How to: Test for Reference Equality (Identity) (C# Programming Guide)</span></span>
<span data-ttu-id="1eee3-103">独自の型で参照の等価性の比較をサポートするためにカスタム ロジックを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1eee3-103">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="1eee3-104">この機能は、すべての型に対して <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 静的メソッドとして用意されています。</span><span class="sxs-lookup"><span data-stu-id="1eee3-104">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="1eee3-105">次の例に、2 つの変数の*参照の等価性*、つまり、それらの変数がメモリ内で同一のオブジェクトを参照しているかどうかを確認する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1eee3-105">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="1eee3-106">また、<xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> が値型に対して常に `false` を返す理由と、文字列が等しいかどうかを確認するために <xref:System.Object.ReferenceEquals%2A> を使用しない理由を例に示します。</span><span class="sxs-lookup"><span data-stu-id="1eee3-106">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eee3-107">例</span><span class="sxs-lookup"><span data-stu-id="1eee3-107">Example</span></span>  
 [!code-csharp[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-test-for-reference-equality-identity_1.cs)]  
  
 <span data-ttu-id="1eee3-108">`Equals` 汎用基底クラスの <xref:System.Object?displayProperty=nameWithType> の実装では、参照が等しいかどうかのチェックを実行しますが、このチェックを使用しないようにお勧めします。クラスがメソッドをオーバーライドする場合、予期した結果が得られない可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="1eee3-108">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="1eee3-109">`==` 演算子と `!=` 演算子についても同様です。</span><span class="sxs-lookup"><span data-stu-id="1eee3-109">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="1eee3-110">参照型を操作しようとしている場合、== および `!=` の既定の動作では参照が等しいかどうかのチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eee3-110">When they are operating on reference types, the default behavior of == and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="1eee3-111">ただし、派生クラスは演算子をオーバーロードすることによって、値が等しいかどうかのチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="1eee3-111">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="1eee3-112">エラーが発生する可能性を最小限に抑えるために、2 つのオブジェクトの参照が等しいかどうかを確認する必要がある場合は、常に <xref:System.Object.ReferenceEquals%2A> を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1eee3-112">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="1eee3-113">同じアセンブリ内の定数文字列は、常に、実行時にインターンされます。</span><span class="sxs-lookup"><span data-stu-id="1eee3-113">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="1eee3-114">つまり、一意のリテラル文字列ごとにそのインスタンスが 1 つだけ保持されます。</span><span class="sxs-lookup"><span data-stu-id="1eee3-114">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="1eee3-115">ただし、ランタイムは実行時に作成された文字列がインターンされることを保証しません。また、異なるアセンブリの 2 つの等しい定数文字列がインターンされることも保証しません。</span><span class="sxs-lookup"><span data-stu-id="1eee3-115">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eee3-116">参照</span><span class="sxs-lookup"><span data-stu-id="1eee3-116">See Also</span></span>  
 [<span data-ttu-id="1eee3-117">等価比較</span><span class="sxs-lookup"><span data-stu-id="1eee3-117">Equality Comparisons</span></span>](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)
