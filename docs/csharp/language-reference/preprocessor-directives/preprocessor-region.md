---
title: "#<a name=\"region-c-reference\"></a>region (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
dev_langs:
- CSharp
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
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
ms.openlocfilehash: f7685d23bc1d40a0d0b6c9ac9a644019e1186eb7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="region-c-reference"></a><span data-ttu-id="80d5d-102">#region (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="80d5d-102">#region (C# Reference)</span></span>
<span data-ttu-id="80d5d-103">`#region` を使用すると、コード ブロックを指定できます。このブロックは、Visual Studio コード エディターの[アウトライン](/visualstudio/ide/outlining)機能を使用して展開や折りたたみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="80d5d-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="80d5d-104">コード ファイルが長い場合は、現在操作している部分に集中できるように 1 つ以上の領域を折りたたむ (非表示にする) ことができると便利です。</span><span class="sxs-lookup"><span data-stu-id="80d5d-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="80d5d-105">次の例では、領域を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="80d5d-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="80d5d-106">コメント</span><span class="sxs-lookup"><span data-stu-id="80d5d-106">Remarks</span></span>  
 <span data-ttu-id="80d5d-107">`#region` ブロックは、[#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) ディレクティブで終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="80d5d-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="80d5d-108">`#region` ブロックは、[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ブロックと重複することはできません。</span><span class="sxs-lookup"><span data-stu-id="80d5d-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="80d5d-109">ただし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="80d5d-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d5d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="80d5d-110">See Also</span></span>  
 <span data-ttu-id="80d5d-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="80d5d-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="80d5d-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="80d5d-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="80d5d-113">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="80d5d-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

