---
title: "#error (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a><span data-ttu-id="b9908-102">#error (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b9908-102">#error (C# Reference)</span></span>
<span data-ttu-id="b9908-103">`#error` を使用すると、コード内の特定の場所からエラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b9908-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="b9908-104">例:</span><span class="sxs-lookup"><span data-stu-id="b9908-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9908-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b9908-105">Remarks</span></span>  
 <span data-ttu-id="b9908-106">`#error` は条件付きディレクティブ内で一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9908-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="b9908-107">[#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) を使用してユーザー定義の警告を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9908-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9908-108">例</span><span class="sxs-lookup"><span data-stu-id="b9908-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9908-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9908-109">See Also</span></span>  
 [<span data-ttu-id="b9908-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b9908-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b9908-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b9908-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b9908-112">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b9908-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
