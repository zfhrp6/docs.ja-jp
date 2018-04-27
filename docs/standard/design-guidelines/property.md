---
title: プロパティのデザイン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6dcb164daea6809f0d0e9c221f182d5019385bc1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="property-design"></a><span data-ttu-id="15dcb-102">プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="15dcb-102">Property Design</span></span>
<span data-ttu-id="15dcb-103">プロパティはメソッドに技術的には非常に似ていますは、使用シナリオの観点からはまったく異なります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="15dcb-104">これらは、スマート フィールドと考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-104">They should be seen as smart fields.</span></span> <span data-ttu-id="15dcb-105">フィールドの呼び出し構文とメソッドの柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="15dcb-106">**✓ しないで**呼び出し元が、プロパティの値を変更すべき場合取得専用のプロパティを作成します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="15dcb-107">留意する場合の種類、プロパティが変更可能な参照型、プロパティは get-only 場合でも、プロパティの値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="15dcb-108">**X しないで**設定専用のプロパティまたはプロパティを get アクセス操作子よりも広範なアクセシビリティを持つ set アクセス操作子を提供します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="15dcb-109">たとえば、プロパティを使用しないパブリック set アクセス操作子と保護された get アクセス操作子を使用します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="15dcb-110">プロパティの get アクセス操作子を提供できない場合は、代わりにメソッドとして機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="15dcb-111">メソッド名での開始を検討してください`Set`内容は指定済みの場合、プロパティに従います。</span><span class="sxs-lookup"><span data-stu-id="15dcb-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="15dcb-112">たとえば、<xref:System.AppDomain>というメソッドを持ち`SetCachePath`という設定専用のプロパティではなく`CachePath`です。</span><span class="sxs-lookup"><span data-stu-id="15dcb-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="15dcb-113">**✓ しないで**既定の設定がセキュリティ ホールや重大な非効率的なコードで発生しないようにする、すべてのプロパティの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="15dcb-114">**✓ しないで**場合でも、この結果、オブジェクトの一時的な無効な状態で、任意の順序で設定するプロパティを許可します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="15dcb-115">通常は、いくつかの値を 1 つのプロパティの無効になるポイントに相互関連する 2 つ以上のプロパティの同じオブジェクトに対して他のプロパティの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="15dcb-116">このような場合、相互に関連するプロパティがオブジェクトで一緒に使用が実際になるまで無効な状態に起因する例外を延期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="15dcb-117">**✓ しないで**プロパティ set アクセス操作子は例外をスローする場合は、以前の値を保持します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="15dcb-118">**避け x**プロパティ get アクセス操作子から例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="15dcb-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="15dcb-119">プロパティの getter は、単純な操作をする必要があり、すべての前提条件にはできません。</span><span class="sxs-lookup"><span data-stu-id="15dcb-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="15dcb-120">場合は、get アクセス操作子は例外をスローできます、その必要があります可能性があります再設計するメソッド。</span><span class="sxs-lookup"><span data-stu-id="15dcb-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="15dcb-121">このルールは、インデクサー、ここで、引数の検証の結果として例外予測には適用されませんに注意してください。</span><span class="sxs-lookup"><span data-stu-id="15dcb-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="15dcb-122">インデックス付きプロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="15dcb-122">Indexed Property Design</span></span>  
 <span data-ttu-id="15dcb-123">インデックス付きプロパティは、パラメーターを持つことができますし、配列のインデックスのような特別な構文を使用して呼び出すことができる特別なプロパティです。</span><span class="sxs-lookup"><span data-stu-id="15dcb-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="15dcb-124">インデックス付きプロパティは、インデクサーとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="15dcb-125">インデクサーは、論理的なコレクション内の項目へのアクセスを提供する Api でのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="15dcb-126">たとえば、文字列は、一連の文字とでインデクサー<xref:System.String?displayProperty=nameWithType>その文字にアクセスするようになりました。</span><span class="sxs-lookup"><span data-stu-id="15dcb-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="15dcb-127">**✓ を検討してください**内部配列に格納されたデータへのアクセスを提供するインデクサーを使用します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="15dcb-128">**✓ を検討してください**項目のコレクションを表す型のインデクサーを提供します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="15dcb-129">**避け x** 1 つ以上のパラメーターを持つプロパティを使用してインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="15dcb-130">設計には、複数のパラメーターが必要とする場合は、プロパティが実際にアクセサーを表す論理的なコレクションにするかどうかを再確認します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="15dcb-131">そうでない場合は、代わりにメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-131">If it does not, use methods instead.</span></span> <span data-ttu-id="15dcb-132">まず、メソッド名で`Get`または`Set`です。</span><span class="sxs-lookup"><span data-stu-id="15dcb-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="15dcb-133">**避け x**以外のパラメーターの型を持つインデクサー <xref:System.Int32?displayProperty=nameWithType>、 <xref:System.Int64?displayProperty=nameWithType>、 <xref:System.String?displayProperty=nameWithType>、 <xref:System.Object?displayProperty=nameWithType>、または列挙型。</span><span class="sxs-lookup"><span data-stu-id="15dcb-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="15dcb-134">デザインには、その他の種類のパラメーターが必要な厳密 API が実際にアクセサーを表す論理的なコレクションにするかどうかを再評価します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="15dcb-135">そうでない場合は、メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-135">If it does not, use a method.</span></span> <span data-ttu-id="15dcb-136">まず、メソッド名で`Get`または`Set`です。</span><span class="sxs-lookup"><span data-stu-id="15dcb-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="15dcb-137">**✓ しないで**名前を使用して`Item`の言うまでもなく、名前がある場合を除き、インデックス付きプロパティ (などを参照してください、<xref:System.String.Chars%2A>プロパティを`System.String`)。</span><span class="sxs-lookup"><span data-stu-id="15dcb-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="15dcb-138">C# の場合、インデクサーは既定では名前付きアイテムです。</span><span class="sxs-lookup"><span data-stu-id="15dcb-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="15dcb-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute>この名前をカスタマイズするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="15dcb-140">**X しないで**インデクサーと意味的に等しいメソッドの両方を提供します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="15dcb-141">**X しないで**1 つの型でのオーバー ロードされたインデクサーの 1 つ以上のファミリを指定します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="15dcb-142">これは、c# コンパイラによって強制されます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="15dcb-143">**X しないで**使用する既定以外のインデックス付きプロパティです。</span><span class="sxs-lookup"><span data-stu-id="15dcb-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="15dcb-144">これは、c# コンパイラによって強制されます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="15dcb-145">プロパティ変更通知イベント</span><span class="sxs-lookup"><span data-stu-id="15dcb-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="15dcb-146">プロパティ値の変更のユーザーに通知するイベントを提供すると便利ですがあります。</span><span class="sxs-lookup"><span data-stu-id="15dcb-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="15dcb-147">たとえば、`System.Windows.Forms.Control`を発生させます、`TextChanged`イベントの値の後にその`Text`プロパティが変更されました。</span><span class="sxs-lookup"><span data-stu-id="15dcb-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="15dcb-148">**✓ を検討してください**大まかな Api (通常、デザイナー コンポーネント) のプロパティ値が変更されたときに通知イベントを変更させるとします。</span><span class="sxs-lookup"><span data-stu-id="15dcb-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="15dcb-149">ユーザーがオブジェクトのプロパティを変更する場合を判断するための適切なシナリオがある場合、オブジェクトは、プロパティの変更通知イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="15dcb-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="15dcb-150">ただし、イベントを発生させるような低レベルの Api の基本型、コレクションなどのオーバーヘッドすべきである可能性はありません。</span><span class="sxs-lookup"><span data-stu-id="15dcb-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="15dcb-151">たとえば、<xref:System.Collections.Generic.List%601>がない新しい項目が一覧に追加されたときに、このようなイベントを発生させると、`Count`プロパティが変更されました。</span><span class="sxs-lookup"><span data-stu-id="15dcb-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="15dcb-152">**✓ を検討してください**外的要因を使用して、プロパティの値が変更されたときに、通知イベントを発生させる変更します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="15dcb-153">何らかの外的要因 (形で以外のオブジェクトでメソッドを呼び出すことにより) を使用してプロパティ値が変更された場合に発生させるイベントことを示すため、開発者に値が変更が変更されました。</span><span class="sxs-lookup"><span data-stu-id="15dcb-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="15dcb-154">良い例は、`Text`テキスト ボックス コントロールのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="15dcb-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="15dcb-155">ユーザーが内のテキストを入力するときに、`TextBox`プロパティの値が自動的に変更します。</span><span class="sxs-lookup"><span data-stu-id="15dcb-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="15dcb-156">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="15dcb-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="15dcb-157">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="15dcb-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15dcb-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="15dcb-158">See Also</span></span>  
 [<span data-ttu-id="15dcb-159">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="15dcb-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="15dcb-160">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="15dcb-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
