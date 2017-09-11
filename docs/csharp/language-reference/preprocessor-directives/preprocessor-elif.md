---
title: "#<a name=\"elif-c-reference\"></a>elif (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7635365222621101253ecb2a3676701c2e6a2b88
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="elif-c-reference"></a><span data-ttu-id="19d11-102">#elif (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="19d11-102">#elif (C# Reference)</span></span>
<span data-ttu-id="19d11-103">`#elif` を使用すると、複合条件付きディレクティブを作成できます。</span><span class="sxs-lookup"><span data-stu-id="19d11-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="19d11-104">`#elif` 式が評価されるのは、先行するディレクティブ式 [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) および `#elif` (オプション) が `true` と評価されなかった場合です。</span><span class="sxs-lookup"><span data-stu-id="19d11-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="19d11-105">`#elif` 式が `true` と評価された場合は、`#elif` と次の条件付きディレクティブの間にあるすべてのコードが、コンパイラによって評価されます。</span><span class="sxs-lookup"><span data-stu-id="19d11-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="19d11-106">例:</span><span class="sxs-lookup"><span data-stu-id="19d11-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="19d11-107">複数のシンボルを評価するときには、`==` (等値)、`!=` (非等値)、`&&` (AND)、および `||` (OR) の演算子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="19d11-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="19d11-108">シンボルと演算子は、かっこを使用してグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="19d11-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19d11-109">コメント</span><span class="sxs-lookup"><span data-stu-id="19d11-109">Remarks</span></span>  
 <span data-ttu-id="19d11-110">`#elif` では、次のように記述した場合と同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="19d11-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="19d11-111">`#elif` を使用する方が簡単です。`#if` には対になる [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が必要ですが、`#elif` では対応する `#endif` が不要なためです。</span><span class="sxs-lookup"><span data-stu-id="19d11-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="19d11-112">`#elif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d11-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d11-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="19d11-113">See Also</span></span>  
 <span data-ttu-id="19d11-114">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="19d11-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="19d11-115">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="19d11-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="19d11-116">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="19d11-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

