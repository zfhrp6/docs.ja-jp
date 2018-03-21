---
title: "メソッドのパラメーター (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="01c11-102">メソッドのパラメーター (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="01c11-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="01c11-103">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) または [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) のないメソッドで宣言されたパラメーターは、呼び出されたメソッドに値で渡されます。</span><span class="sxs-lookup"><span data-stu-id="01c11-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="01c11-104">メソッドでその値を変更できますが、呼び出し元のプロシージャに制御が渡されるときに、変更された値は保持されません。</span><span class="sxs-lookup"><span data-stu-id="01c11-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="01c11-105">メソッド パラメーターのキーワードを使用して、この動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="01c11-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="01c11-106">ここでは、メソッドのパラメーターを宣言するときに使用できるキーワードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01c11-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="01c11-107">params</span><span class="sxs-lookup"><span data-stu-id="01c11-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="01c11-108">in</span><span class="sxs-lookup"><span data-stu-id="01c11-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="01c11-109">ref</span><span class="sxs-lookup"><span data-stu-id="01c11-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="01c11-110">out</span><span class="sxs-lookup"><span data-stu-id="01c11-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="01c11-111">参照</span><span class="sxs-lookup"><span data-stu-id="01c11-111">See Also</span></span>  
 [<span data-ttu-id="01c11-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="01c11-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="01c11-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="01c11-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="01c11-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="01c11-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
