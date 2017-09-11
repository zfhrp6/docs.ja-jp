---
title: "メソッドのパラメーター (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 8
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
ms.openlocfilehash: 4ba57e1a9e904befe11ff41796c987bd8f93b081
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="4de57-102">メソッドのパラメーター (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4de57-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="4de57-103">パラメーターが、[ref](../../../csharp/language-reference/keywords/ref.md) または [out](../../../csharp/language-reference/keywords/out.md) のないメソッドで宣言されている場合、パラメーターは関連付けられた値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="4de57-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="4de57-104">メソッドでその値を変更できますが、呼び出し元のプロシージャに制御が渡されるときに、変更された値は保持されません。</span><span class="sxs-lookup"><span data-stu-id="4de57-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="4de57-105">メソッド パラメーターのキーワードを使用して、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4de57-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="4de57-106">ここでは、メソッドのパラメーターを宣言するときに使用できるキーワードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4de57-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="4de57-107">params</span><span class="sxs-lookup"><span data-stu-id="4de57-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="4de57-108">ref</span><span class="sxs-lookup"><span data-stu-id="4de57-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="4de57-109">out</span><span class="sxs-lookup"><span data-stu-id="4de57-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="4de57-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4de57-110">See Also</span></span>  
 <span data-ttu-id="4de57-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4de57-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4de57-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4de57-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="4de57-113">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="4de57-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

