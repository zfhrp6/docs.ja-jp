---
title: '#error (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="error-c-reference"></a><span data-ttu-id="8976a-102">#error (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8976a-102">#error (C# Reference)</span></span>
<span data-ttu-id="8976a-103">`#error` を使用すると、コード内の特定の場所からエラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="8976a-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="8976a-104">例:</span><span class="sxs-lookup"><span data-stu-id="8976a-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="8976a-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8976a-105">Remarks</span></span>  
 <span data-ttu-id="8976a-106">`#error` は条件付きディレクティブ内で一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8976a-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="8976a-107">[#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md) を使用してユーザー定義の警告を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8976a-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8976a-108">例</span><span class="sxs-lookup"><span data-stu-id="8976a-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8976a-109">参照</span><span class="sxs-lookup"><span data-stu-id="8976a-109">See Also</span></span>  
 [<span data-ttu-id="8976a-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8976a-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8976a-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8976a-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8976a-112">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="8976a-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
