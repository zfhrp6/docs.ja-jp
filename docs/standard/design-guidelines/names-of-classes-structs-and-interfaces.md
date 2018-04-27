---
title: クラス、構造体、およびインターフェイスの名前
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bcb3d1c636c8f846be8290738f322f36e09c9dad
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="d13b1-102">クラス、構造体、およびインターフェイスの名前</span><span class="sxs-lookup"><span data-stu-id="d13b1-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="d13b1-103">次の名前付けのガイドラインは、一般的な種類の名前付けに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d13b1-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="d13b1-104">**✓ しないで**名前をクラスと構造体には名詞または名詞句を使用して pascal 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="d13b1-105">これは、動詞句とという名前のメソッドと型名を区別します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="d13b1-106">**✓ しないで**形容詞句、または場合によっては名詞または名詞句とインターフェイスの名前します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="d13b1-107">名詞や名詞句を付けることはほとんどなく、種類必要がある、抽象クラスとインターフェイスではなくを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d13b1-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="d13b1-108">**X しないで**クラス名のプレフィックス ("C"など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="d13b1-109">**✓ を検討してください**基底クラスの名前のクラスを派生の名前を終了します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="d13b1-110">これは非常に読み取り可能であり、リレーションシップを明確に説明します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="d13b1-111">コードでは次の例を示します:`ArgumentOutOfRangeException`は一種の`Exception`、および`SerializableAttribute`は一種の`Attribute`します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="d13b1-112">ただし、することが重要です。 このガイドラインを適用することで、適切な判断たとえば、`Button`クラスは、一種の`Control`イベントが`Control`その名前が表示されません。</span><span class="sxs-lookup"><span data-stu-id="d13b1-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="d13b1-113">**✓ しないで**インターフェイス名のプレフィックス文字では、型がインターフェイスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="d13b1-114">たとえば、 `IComponent` (わかりやすい名詞) `ICustomAttributeProvider` (名詞句)、および`IPersistable`(形容詞) 適切なインターフェイス名は、します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="d13b1-115">同様に他の種類名の省略形を回避します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="d13b1-116">**✓ しないで**だけで、"I"プレフィックスのインターフェイスの名前、クラスがインターフェイスの標準的な実装であるクラス – インターフェイスのペアを定義するときに名前が異なることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d13b1-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="d13b1-117">ジェネリック型パラメーターの名前</span><span class="sxs-lookup"><span data-stu-id="d13b1-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="d13b1-118">ジェネリックは、.NET Framework 2.0 に追加されました。</span><span class="sxs-lookup"><span data-stu-id="d13b1-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="d13b1-119">機能には、新しいと呼ばれる識別子の種類が導入されました。*パラメーター入力*です。</span><span class="sxs-lookup"><span data-stu-id="d13b1-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="d13b1-120">**✓ しないで**1 文字の名前が完全にわかり、わかりやすい名前と値を追加していない場合を除き、わかりやすい名前を持つジェネリック型パラメーターの名前します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="d13b1-121">**✓ を検討してください**を使用して`T`の 1 文字の型パラメーターを 1 つの種類の型パラメーター名として。</span><span class="sxs-lookup"><span data-stu-id="d13b1-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="d13b1-122">**✓ しないで**説明的な型パラメーター名をプレフィックス`T`です。</span><span class="sxs-lookup"><span data-stu-id="d13b1-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession{  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="d13b1-123">**✓ を検討してください**制約を示す名前、パラメーターの型パラメーター上に配置します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="d13b1-124">など、パラメーターに対する制約として`ISession`という`TSession`です。</span><span class="sxs-lookup"><span data-stu-id="d13b1-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="d13b1-125">一般的な種類の名前</span><span class="sxs-lookup"><span data-stu-id="d13b1-125">Names of Common Types</span></span>  
 <span data-ttu-id="d13b1-126">**✓ しないで**から派生または特定の .NET Framework 型を実装する型の名前を付けるときは、次の表に説明されているガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="d13b1-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="d13b1-127">基本型</span><span class="sxs-lookup"><span data-stu-id="d13b1-127">Base Type</span></span>|<span data-ttu-id="d13b1-128">派生実装する型のガイドライン</span><span class="sxs-lookup"><span data-stu-id="d13b1-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="d13b1-129">**✓ しないで**カスタム属性クラスの名前にサフィックス"Attribute"を追加します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="d13b1-130">**✓ しないで**イベントで使用されるデリゲートの名前にサフィックス"EventHandler"を追加します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="d13b1-131">**✓ しないで**以外のイベント ハンドラーとして使用されているデリゲートの名前に"Callback"サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="d13b1-132">**X しないで**「代理」サフィックスをデリゲートに追加します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="d13b1-133">**✓ しないで**"EventArgs です"というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="d13b1-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="d13b1-134">**X しないで**代わりに使用する言語でサポートされているキーワードを使用して; たとえば、C# の場合、次のように使用します。 このクラスから派生、`enum`キーワード。</span><span class="sxs-lookup"><span data-stu-id="d13b1-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="d13b1-135">**X しないで**「列挙」または"Flag"サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="d13b1-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="d13b1-136">**✓ しないで**"Exception"サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="d13b1-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="d13b1-137">**✓ しないで**「ディクショナリ」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="d13b1-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="d13b1-138">なお`IDictionary`コレクションの特定の種類が、このガイドラインに続くコレクションのより一般的なガイドラインよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="d13b1-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="d13b1-139">**✓ しないで**「コレクション」サフィックスを追加</span><span class="sxs-lookup"><span data-stu-id="d13b1-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="d13b1-140">**✓ しないで**「ストリームです」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="d13b1-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="d13b1-141">**✓ しないで**「権限」というサフィックスを追加。</span><span class="sxs-lookup"><span data-stu-id="d13b1-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="d13b1-142">列挙体の名前を付ける</span><span class="sxs-lookup"><span data-stu-id="d13b1-142">Naming Enumerations</span></span>  
 <span data-ttu-id="d13b1-143">一般に列挙型 (列挙型とも呼ばれます) の名前は、標準的な型の名前付け規則 (pascal 表記を使用など) を従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d13b1-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="d13b1-144">ただし、これには具体的には列挙型に適用される追加のガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="d13b1-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="d13b1-145">**✓ しないで**ビット フィールドがその値がない限り、列挙体の単数形の型名を使用します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="d13b1-146">**✓ しないで**ビット フィールドを持つ列挙体の複数形の型名を使用して値として、フラグ列挙型とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d13b1-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="d13b1-147">**X しないで**列挙型の型名で、「列挙」サフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="d13b1-148">**X しないで**「フラグを設定」を使用して、または"Flags"サフィックス列挙型では、名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="d13b1-149">**X しないで**リッチ テキストの列挙型などの列挙値の名前 (例:"ad"ADO 列挙型の場合。)、"rtf"に対して、プレフィックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d13b1-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="d13b1-150">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d13b1-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d13b1-151">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="d13b1-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13b1-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="d13b1-152">See Also</span></span>  
 [<span data-ttu-id="d13b1-153">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="d13b1-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="d13b1-154">名前付けのガイドライン</span><span class="sxs-lookup"><span data-stu-id="d13b1-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
