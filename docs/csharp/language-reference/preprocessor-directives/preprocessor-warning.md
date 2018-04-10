---
title: '#warning (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8145c4a62d5179d6fa46e27186d83fc0108939d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="warning-c-reference"></a><span data-ttu-id="d15b5-102">#warning (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d15b5-102">#warning (C# Reference)</span></span>
<span data-ttu-id="d15b5-103">`#warning` を使用すると、コード内の特定の場所からレベル 1 の警告を生成できます。</span><span class="sxs-lookup"><span data-stu-id="d15b5-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="d15b5-104">例:</span><span class="sxs-lookup"><span data-stu-id="d15b5-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="d15b5-105">コメント</span><span class="sxs-lookup"><span data-stu-id="d15b5-105">Remarks</span></span>  
 <span data-ttu-id="d15b5-106">`#warning` は条件付きディレクティブ内で一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d15b5-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="d15b5-107">[#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) を使用してユーザー定義のエラーを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d15b5-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d15b5-108">例</span><span class="sxs-lookup"><span data-stu-id="d15b5-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d15b5-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="d15b5-109">See Also</span></span>  
 [<span data-ttu-id="d15b5-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d15b5-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d15b5-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="d15b5-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d15b5-112">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="d15b5-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
