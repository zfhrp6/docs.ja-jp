---
title: "メソッドのパラメーター (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="f2543-102">メソッドのパラメーター (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f2543-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="f2543-103">パラメーターが、[ref](../../../csharp/language-reference/keywords/ref.md) または [out](../../../csharp/language-reference/keywords/out.md) のないメソッドで宣言されている場合、パラメーターは関連付けられた値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="f2543-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="f2543-104">メソッドでその値を変更できますが、呼び出し元のプロシージャに制御が渡されるときに、変更された値は保持されません。</span><span class="sxs-lookup"><span data-stu-id="f2543-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="f2543-105">メソッド パラメーターのキーワードを使用して、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="f2543-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="f2543-106">ここでは、メソッドのパラメーターを宣言するときに使用できるキーワードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f2543-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="f2543-107">params</span><span class="sxs-lookup"><span data-stu-id="f2543-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="f2543-108">ref</span><span class="sxs-lookup"><span data-stu-id="f2543-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="f2543-109">out</span><span class="sxs-lookup"><span data-stu-id="f2543-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2543-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2543-110">See Also</span></span>  
 [<span data-ttu-id="f2543-111">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f2543-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f2543-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f2543-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2543-113">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="f2543-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
