---
title: "event (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
dev_langs:
- CSharp
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
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
ms.openlocfilehash: 674e36625a68243afff75f6c5028309dc7aff02a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="event-c-reference"></a><span data-ttu-id="6f29a-102">event (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6f29a-102">event (C# Reference)</span></span>
<span data-ttu-id="6f29a-103">`event` キーワードを使用し、パブリッシャー クラス内にイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6f29a-103">The `event` keyword is used to declare an event in a publisher class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f29a-104">例</span><span class="sxs-lookup"><span data-stu-id="6f29a-104">Example</span></span>  
 <span data-ttu-id="6f29a-105">次の例では、基になるデリゲート型として <xref:System.EventHandler> を使用するイベントを宣言し、発生させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f29a-105">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="6f29a-106">完全なコード例については、「[方法: .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)」を参照してください。完全なコード例では、ジェネリック <xref:System.EventHandler%601> デリゲート型の使用方法と、イベントをサブスクライブして、イベント ハンドラー メソッドを作成する方法も確認できます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-106">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>  
  
 <span data-ttu-id="6f29a-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6f29a-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span></span>  
  
 <span data-ttu-id="6f29a-108">イベントは、宣言元 (パブリッシャー クラス) のクラスまたは構造体内でしか呼び出せない特殊なマルチキャスト デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="6f29a-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="6f29a-109">他のクラスまたは構造体がイベントを受信登録した場合、パブリッシャー クラスがイベントを発生させると、他のクラスまたは構造体のイベント ハンドラー メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="6f29a-110">詳細およびコード例については、「[イベント](../../../csharp/programming-guide/events/index.md)」および「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f29a-110">For more information and code examples, see [Events](../../../csharp/programming-guide/events/index.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
 <span data-ttu-id="6f29a-111">イベントは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected internal` としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-111">Events can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="6f29a-112">これらのアクセス修飾子により、クラスのユーザーがイベントにアクセスする方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="6f29a-113">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f29a-113">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="keywords-and-events"></a><span data-ttu-id="6f29a-114">キーワードとイベント</span><span class="sxs-lookup"><span data-stu-id="6f29a-114">Keywords and Events</span></span>  
 <span data-ttu-id="6f29a-115">イベントには次のキーワードが適用されます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-115">The following keywords apply to events.</span></span>  
  
|<span data-ttu-id="6f29a-116">キーワード</span><span class="sxs-lookup"><span data-stu-id="6f29a-116">Keyword</span></span>|<span data-ttu-id="6f29a-117">説明</span><span class="sxs-lookup"><span data-stu-id="6f29a-117">Description</span></span>|<span data-ttu-id="6f29a-118">詳細情報</span><span class="sxs-lookup"><span data-stu-id="6f29a-118">For more information</span></span>|  
|-------------|-----------------|--------------------------|  
|[<span data-ttu-id="6f29a-119">static</span><span class="sxs-lookup"><span data-stu-id="6f29a-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="6f29a-120">クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもイベントを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="6f29a-121">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="6f29a-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[<span data-ttu-id="6f29a-122">virtual</span><span class="sxs-lookup"><span data-stu-id="6f29a-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="6f29a-123">[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用してイベントの動作をオーバーライドすることを派生クラスに許可します。</span><span class="sxs-lookup"><span data-stu-id="6f29a-123">Allows derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span>|[<span data-ttu-id="6f29a-124">継承</span><span class="sxs-lookup"><span data-stu-id="6f29a-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[<span data-ttu-id="6f29a-125">sealed</span><span class="sxs-lookup"><span data-stu-id="6f29a-125">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="6f29a-126">派生クラスでは、それが仮想ではなくなったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="6f29a-126">Specifies that for derived classes it is no longer virtual.</span></span>||  
|[<span data-ttu-id="6f29a-127">abstract</span><span class="sxs-lookup"><span data-stu-id="6f29a-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="6f29a-128">コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。したがって、派生クラスは固有の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||  
  
 <span data-ttu-id="6f29a-129">イベントは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的イベントとして宣言されることもあります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-129">An event may be declared as a static event by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="6f29a-130">その場合、クラスのインスタンスが存在しなくても、呼び出し元がいつでもイベントを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="6f29a-131">詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f29a-131">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="6f29a-132">イベントは、[virtual](../../../csharp/language-reference/keywords/virtual.md) キーワードを使用して仮想イベントとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-132">An event can be marked as a virtual event by using the [virtual](../../../csharp/language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="6f29a-133">その場合、派生クラスでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用してイベントの動作をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="6f29a-133">This enables derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="6f29a-134">詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f29a-134">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="6f29a-135">仮想イベントをオーバーライドするイベントは、[sealed](../../../csharp/language-reference/keywords/sealed.md) にすることもできます。その場合、派生クラスでは、イベントが仮想でなくなります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-135">An event overriding a virtual event can also be [sealed](../../../csharp/language-reference/keywords/sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="6f29a-136">最後に、イベントは [abstract](../../../csharp/language-reference/keywords/abstract.md) として宣言できます。その場合、コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。</span><span class="sxs-lookup"><span data-stu-id="6f29a-136">Lastly, an event can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="6f29a-137">したがって、派生クラスごとに固有の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f29a-137">Therefore derived classes must provide their own implementation.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6f29a-138">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6f29a-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6f29a-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f29a-139">See Also</span></span>  
 <span data-ttu-id="6f29a-140">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6f29a-141">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6f29a-142">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-142">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="6f29a-143">[add](../../../csharp/language-reference/keywords/add.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-143">[add](../../../csharp/language-reference/keywords/add.md) </span></span>  
 <span data-ttu-id="6f29a-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span></span>  
 <span data-ttu-id="6f29a-145">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="6f29a-145">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="6f29a-146">方法 : デリゲートを結合する (マルチキャスト デリゲート)</span><span class="sxs-lookup"><span data-stu-id="6f29a-146">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

