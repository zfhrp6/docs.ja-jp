---
title: "修飾子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- keywords [C#], modifiers
- modifiers [C#]
ms.assetid: c96691dd-b357-49ec-b5ae-03ca214fadfb
caps.latest.revision: 18
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
ms.openlocfilehash: 9e2e7e5e3907ac9bb66676e749ddd55a8ac4836c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="modifiers-c-reference"></a><span data-ttu-id="81cbb-102">修飾子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="81cbb-102">Modifiers (C# Reference)</span></span>
<span data-ttu-id="81cbb-103">修飾子は、型および型メンバーの宣言を修飾するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="81cbb-103">Modifiers are used to modify declarations of types and type members.</span></span> <span data-ttu-id="81cbb-104">ここでは、C# の修飾子について説明します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-104">This section introduces the C# modifiers.</span></span>  
  
|<span data-ttu-id="81cbb-105">修飾子</span><span class="sxs-lookup"><span data-stu-id="81cbb-105">Modifier</span></span>|<span data-ttu-id="81cbb-106">目的</span><span class="sxs-lookup"><span data-stu-id="81cbb-106">Purpose</span></span>|  
|--------------|-------------|  
|[<span data-ttu-id="81cbb-107">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="81cbb-107">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)<br /><br /> <span data-ttu-id="81cbb-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span><span class="sxs-lookup"><span data-stu-id="81cbb-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span></span><br /><span data-ttu-id="81cbb-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span><span class="sxs-lookup"><span data-stu-id="81cbb-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span></span><br /><span data-ttu-id="81cbb-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span><span class="sxs-lookup"><span data-stu-id="81cbb-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span></span><br /><span data-ttu-id="81cbb-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span><span class="sxs-lookup"><span data-stu-id="81cbb-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span></span>|<span data-ttu-id="81cbb-112">型および型のメンバーで宣言されたアクセシビリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-112">Specifies the declared accessibility of types and type members.</span></span>|  
|[<span data-ttu-id="81cbb-113">abstract</span><span class="sxs-lookup"><span data-stu-id="81cbb-113">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="81cbb-114">クラスが、他のクラスの基本クラスになるためだけのものであることを示します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-114">Indicates that a class is intended only to be a base class of other classes.</span></span>|  
|[<span data-ttu-id="81cbb-115">async</span><span class="sxs-lookup"><span data-stu-id="81cbb-115">async</span></span>](../../../csharp/language-reference/keywords/async.md)|<span data-ttu-id="81cbb-116">修飾されたメソッド、ラムダ式、または匿名メソッドが非同期であることを示します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-116">Indicates that the modified method, lambda expression, or anonymous method is asynchronous.</span></span>|  
|[<span data-ttu-id="81cbb-117">const</span><span class="sxs-lookup"><span data-stu-id="81cbb-117">const</span></span>](../../../csharp/language-reference/keywords/const.md)|<span data-ttu-id="81cbb-118">フィールドまたはローカル変数の値が変更されないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-118">Specifies that the value of the field or the local variable cannot be modified.</span></span>|  
|[<span data-ttu-id="81cbb-119">event</span><span class="sxs-lookup"><span data-stu-id="81cbb-119">event</span></span>](../../../csharp/language-reference/keywords/event.md)|<span data-ttu-id="81cbb-120">イベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-120">Declares an event.</span></span>|  
|[<span data-ttu-id="81cbb-121">extern</span><span class="sxs-lookup"><span data-stu-id="81cbb-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)|<span data-ttu-id="81cbb-122">メソッドが外部で実装されることを示します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-122">Indicates that the method is implemented externally.</span></span>|  
|[<span data-ttu-id="81cbb-123">new</span><span class="sxs-lookup"><span data-stu-id="81cbb-123">new</span></span>](../../../csharp/language-reference/keywords/new.md)|<span data-ttu-id="81cbb-124">基底クラスから継承されたメンバーを明示的に隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="81cbb-124">Explicitly hides a member inherited from a base class.</span></span>|  
|[<span data-ttu-id="81cbb-125">override</span><span class="sxs-lookup"><span data-stu-id="81cbb-125">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="81cbb-126">基本クラスから継承された仮想メンバーの新しい実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-126">Provides a new implementation of a virtual member inherited from a base class.</span></span>|  
|[<span data-ttu-id="81cbb-127">partial</span><span class="sxs-lookup"><span data-stu-id="81cbb-127">partial</span></span>](../../../csharp/language-reference/keywords/partial-type.md)|<span data-ttu-id="81cbb-128">同一アセンブリに部分クラス、部分構造体、または部分メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-128">Defines partial classes, structs and methods throughout the same assembly.</span></span>|  
|[<span data-ttu-id="81cbb-129">readonly</span><span class="sxs-lookup"><span data-stu-id="81cbb-129">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)|<span data-ttu-id="81cbb-130">フィールドを宣言します。このフィールドは、宣言の一部として、または同じクラスのコンストラクター内でだけ、値の代入ができます。</span><span class="sxs-lookup"><span data-stu-id="81cbb-130">Declares a field that can only be assigned values as part of the declaration or in a constructor in the same class.</span></span>|  
|[<span data-ttu-id="81cbb-131">sealed</span><span class="sxs-lookup"><span data-stu-id="81cbb-131">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="81cbb-132">クラスの継承ができないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-132">Specifies that a class cannot be inherited.</span></span>|  
|[<span data-ttu-id="81cbb-133">static</span><span class="sxs-lookup"><span data-stu-id="81cbb-133">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="81cbb-134">特定のオブジェクトではなく、型自体に所属するメンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-134">Declares a member that belongs to the type itself instead of to a specific object.</span></span>|  
|[<span data-ttu-id="81cbb-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="81cbb-135">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)|<span data-ttu-id="81cbb-136">安全ではないコンテキストを宣言します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-136">Declares an unsafe context.</span></span>|  
|[<span data-ttu-id="81cbb-137">virtual</span><span class="sxs-lookup"><span data-stu-id="81cbb-137">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="81cbb-138">メソッドまたはアクセサーを宣言します。これらの実装は、派生クラスでオーバーライドするメンバーによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="81cbb-138">Declares a method or an accessor whose implementation can be changed by an overriding member in a derived class.</span></span>|  
|[<span data-ttu-id="81cbb-139">volatile</span><span class="sxs-lookup"><span data-stu-id="81cbb-139">volatile</span></span>](../../../csharp/language-reference/keywords/volatile.md)|<span data-ttu-id="81cbb-140">オペレーティング システム、ハードウェア、現在実行中のスレッドなどによって、フィールドがプログラム中で変更される場合があることを示します。</span><span class="sxs-lookup"><span data-stu-id="81cbb-140">Indicates that a field can be modified in the program by something such as the operating system, the hardware, or a concurrently executing thread.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81cbb-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="81cbb-141">See Also</span></span>  
 <span data-ttu-id="81cbb-142">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="81cbb-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="81cbb-143">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="81cbb-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="81cbb-144">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="81cbb-144">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

