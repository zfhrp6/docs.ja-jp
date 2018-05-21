---
title: '#elif (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: ecc5c4b48790d0cb6825883922f3903414bb2b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="elif-c-reference"></a><span data-ttu-id="b7204-102">#elif (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b7204-102">#elif (C# Reference)</span></span>
<span data-ttu-id="b7204-103">`#elif` を使用すると、複合条件付きディレクティブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b7204-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="b7204-104">`#elif` 式が評価されるのは、先行するディレクティブ式 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) および `#elif` (オプション) が `true` と評価されなかった場合です。</span><span class="sxs-lookup"><span data-stu-id="b7204-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="b7204-105">`#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。</span><span class="sxs-lookup"><span data-stu-id="b7204-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="b7204-106">例:</span><span class="sxs-lookup"><span data-stu-id="b7204-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="b7204-107">複数のシンボルを評価するときには、`==` (等値)、`!=` (非等値)、`&&` (AND)、および `||` (OR) の演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7204-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="b7204-108">シンボルと演算子は、かっこを使用してグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="b7204-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7204-109">コメント</span><span class="sxs-lookup"><span data-stu-id="b7204-109">Remarks</span></span>  
 <span data-ttu-id="b7204-110">`#elif` では、次のように記述した場合と同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="b7204-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="b7204-111">`#elif` を使用する方が簡単です。`#if` には対になる [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が必要ですが、`#elif` では対応する `#endif` が不要なためです。</span><span class="sxs-lookup"><span data-stu-id="b7204-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="b7204-112">`#elif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7204-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7204-113">参照</span><span class="sxs-lookup"><span data-stu-id="b7204-113">See Also</span></span>  
 [<span data-ttu-id="b7204-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b7204-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b7204-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b7204-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7204-116">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b7204-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
