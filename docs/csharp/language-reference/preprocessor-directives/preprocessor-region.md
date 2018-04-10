---
title: '#region (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="36d66-102">#region (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="36d66-102">#region (C# Reference)</span></span>
<span data-ttu-id="36d66-103">`#region` を使用すると、コード ブロックを指定できます。このブロックは、Visual Studio コード エディターの[アウトライン](/visualstudio/ide/outlining)機能を使用して展開や折りたたみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="36d66-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="36d66-104">コード ファイルが長い場合は、現在操作している部分に集中できるように 1 つ以上の領域を折りたたむ (非表示にする) ことができると便利です。</span><span class="sxs-lookup"><span data-stu-id="36d66-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="36d66-105">次の例では、領域を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="36d66-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="36d66-106">コメント</span><span class="sxs-lookup"><span data-stu-id="36d66-106">Remarks</span></span>  
 <span data-ttu-id="36d66-107">`#region` ブロックは、[#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) ディレクティブで終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="36d66-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="36d66-108">`#region` ブロックは、[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ブロックと重複することはできません。</span><span class="sxs-lookup"><span data-stu-id="36d66-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="36d66-109">ただし、`#region` ブロックを `#if` ブロック内に入れ子にしたり、`#if` ブロックを `#region` ブロック内に入れ子にしたりすることはできます。</span><span class="sxs-lookup"><span data-stu-id="36d66-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d66-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="36d66-110">See Also</span></span>  
 [<span data-ttu-id="36d66-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="36d66-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="36d66-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="36d66-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="36d66-113">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="36d66-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
