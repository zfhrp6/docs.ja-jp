---
title: "列挙型デザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7e1686dca2b96e339917b6dd4861f0f43d20d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enum-design"></a><span data-ttu-id="b1601-102">列挙型デザイン</span><span class="sxs-lookup"><span data-stu-id="b1601-102">Enum Design</span></span>
<span data-ttu-id="b1601-103">列挙型は、特殊な値の型です。</span><span class="sxs-lookup"><span data-stu-id="b1601-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="b1601-104">列挙型の 2 種類があります。 単純な列挙型、およびフラグ列挙型。</span><span class="sxs-lookup"><span data-stu-id="b1601-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="b1601-105">単純な列挙型は、選択肢の小さな閉じたセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b1601-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="b1601-106">単純な列挙型の一般的な例は、色のセットです。</span><span class="sxs-lookup"><span data-stu-id="b1601-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="b1601-107">フラグ列挙型は、列挙値のビットごとの演算をサポートするために設計されています。</span><span class="sxs-lookup"><span data-stu-id="b1601-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="b1601-108">フラグ列挙体の一般的な例では、オプションの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="b1601-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="b1601-109">**✓ しないで**を厳密に型パラメーター、プロパティ、列挙型を使用し、戻り値のセットを表す値です。</span><span class="sxs-lookup"><span data-stu-id="b1601-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="b1601-110">**✓ しないで**列挙型を静的な定数の代わりに使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b1601-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="b1601-111">**X しないで**(など、オペレーティング システムのバージョン、友人などの名前)、開いているセットの列挙型を使用します。</span><span class="sxs-lookup"><span data-stu-id="b1601-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="b1601-112">**X しないで**将来使用するためのものでは予約されている列挙値を提供します。</span><span class="sxs-lookup"><span data-stu-id="b1601-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="b1601-113">値は、後の段階で既存の列挙体を常に単純に追加できます。</span><span class="sxs-lookup"><span data-stu-id="b1601-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="b1601-114">参照してください[列挙体に値を追加する](#add_value)列挙型に値を追加の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="b1601-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="b1601-115">予約済みの値は実際の値のセットを汚染をユーザー エラーが発生する傾向があるだけです。</span><span class="sxs-lookup"><span data-stu-id="b1601-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="b1601-116">**避け x** 1 つだけの値を持つ列挙型を公開することです。</span><span class="sxs-lookup"><span data-stu-id="b1601-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="b1601-117">C Api の将来の機能拡張を確保するための一般的な方法では、メソッドのシグネチャに予約されているパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="b1601-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="b1601-118">このような予約済みのパラメーターは、1 つの既定値を持つ列挙型として表現できます。</span><span class="sxs-lookup"><span data-stu-id="b1601-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="b1601-119">これは、マネージ Api でない実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1601-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="b1601-120">メソッドのオーバー ロードでは、パラメーター今後のリリースで追加できます。</span><span class="sxs-lookup"><span data-stu-id="b1601-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="b1601-121">**X しないで**enum で sentinel 値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b1601-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="b1601-122">フレームワークの開発者に役立つ場合がありますが、sentinel 値は、フレームワークのユーザーが混乱です。</span><span class="sxs-lookup"><span data-stu-id="b1601-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="b1601-123">列挙型で表されるセットから、値のいずれかがではなく、列挙型の状態を追跡するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b1601-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="b1601-124">**✓ しないで**単純な列挙型のゼロの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b1601-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="b1601-125">値を"None"のように呼び出すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b1601-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="b1601-126">このような値がこの特定の列挙型に適切でない場合、列挙型の最も一般的な既定値は、基になる値の 0 割り当て必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1601-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="b1601-127">**✓ を検討してください**を使用して<xref:System.Int32>(ほとんどのプログラミング言語の既定値) enum の基になる型として、次のいずれかが当てはまる場合を除き、します。</span><span class="sxs-lookup"><span data-stu-id="b1601-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="b1601-128">列挙型フラグ列挙は、32 を超えるフラグ、または将来の詳細が見込まれるしました。</span><span class="sxs-lookup"><span data-stu-id="b1601-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="b1601-129">基になる型が必要でも異なっている<xref:System.Int32>のサイズの異なる列挙型を指定してください。 アンマネージ コードと相互運用性を容易にします。</span><span class="sxs-lookup"><span data-stu-id="b1601-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="b1601-130">小さな基になる型は、スペースで大幅に節約になります。</span><span class="sxs-lookup"><span data-stu-id="b1601-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="b1601-131">制御フローの引数として主に使用される列挙型の場合、ほとんど違いは、サイズします。</span><span class="sxs-lookup"><span data-stu-id="b1601-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="b1601-132">サイズ削減量が大幅な可能性がある場合。</span><span class="sxs-lookup"><span data-stu-id="b1601-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="b1601-133">非常に頻繁にインスタンス化された構造体またはクラス内のフィールドとして使用される列挙型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="b1601-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="b1601-134">ユーザー インスタンスの列挙の大きな配列またはコレクションを作成するはずです。</span><span class="sxs-lookup"><span data-stu-id="b1601-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="b1601-135">シリアル化される列挙型のインスタンスの数が多いはずです。</span><span class="sxs-lookup"><span data-stu-id="b1601-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="b1601-136">インメモリ使用量について管理対象のオブジェクトを常に注意してください`DWORD`-固定されているため、効果的に必要な複数の列挙型またはインスタンスの合計サイズは常にあるために、設定を変えるのために小さな列挙型でをパックするインスタンスで他の小規模の構造体まで丸めた後に、`DWORD`です。</span><span class="sxs-lookup"><span data-stu-id="b1601-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="b1601-137">**✓ しないで**フラグの列挙型には複数形の名詞または名詞句と単数形の名詞または名詞句と単純な列挙型の名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="b1601-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="b1601-138">**X しないで**拡張<xref:System.Enum?displayProperty=nameWithType>直接です。</span><span class="sxs-lookup"><span data-stu-id="b1601-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="b1601-139"><xref:System.Enum?displayProperty=nameWithType>特殊な種類で使用、CLR ユーザー定義列挙型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1601-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="b1601-140">ほとんどのプログラミング言語では、この機能にアクセスできるプログラミング要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="b1601-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="b1601-141">たとえば、c# では、`enum`列挙体を定義するキーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1601-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="b1601-142">設計のフラグ列挙型</span><span class="sxs-lookup"><span data-stu-id="b1601-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="b1601-143">**✓ しないで**適用、<xref:System.FlagsAttribute?displayProperty=nameWithType>フラグ列挙体にします。</span><span class="sxs-lookup"><span data-stu-id="b1601-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="b1601-144">単純な列挙体にはこの属性は適用されません。</span><span class="sxs-lookup"><span data-stu-id="b1601-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="b1601-145">**✓ しないで**フラグ列挙値に 2 の累乗を使用して、自由に組み合わせてことができます、ビットごとの OR 演算を使用しているためです。</span><span class="sxs-lookup"><span data-stu-id="b1601-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="b1601-146">**✓ を検討してください**フラグの組み合わせを使用してよくの特別な enum 値を提供します。</span><span class="sxs-lookup"><span data-stu-id="b1601-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="b1601-147">ビットごとの演算は高度な概念することはできません、単純なタスク</span><span class="sxs-lookup"><span data-stu-id="b1601-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="b1601-148"><xref:System.IO.FileAccess.ReadWrite>このような特殊な値の例を示します。</span><span class="sxs-lookup"><span data-stu-id="b1601-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="b1601-149">**避け x**特定の値の組み合わせは有効なフラグ列挙型を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1601-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="b1601-150">**避け x**値が「すべてのフラグをクリアする」を表し、次のガイドラインで規定された方法、適切に名前がない限り、列挙型値ゼロのフラグを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b1601-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="b1601-151">**✓ しないで**フラグ列挙型のゼロ値の名前を付けます`None`です。</span><span class="sxs-lookup"><span data-stu-id="b1601-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="b1601-152">場合は、フラグ列挙型値必要があります常に意味「すべてのフラグはクリアされます」</span><span class="sxs-lookup"><span data-stu-id="b1601-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="b1601-153">列挙型に値を追加</span><span class="sxs-lookup"><span data-stu-id="b1601-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="b1601-154">このコマンドは、既に出荷した後に、列挙型に値を追加する必要があることを検出するごく一般的です。</span><span class="sxs-lookup"><span data-stu-id="b1601-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="b1601-155">潜在的なアプリケーションの互換性問題新しく追加された値が既存の API から返されるためには適切に記述されたアプリケーションで、新しい値を正しく処理されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b1601-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="b1601-156">**✓ を検討してください**小さい互換性上のリスクに関係なく、列挙型に値を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1601-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="b1601-157">列挙型への追加によるアプリケーションの互換性に関する実際のデータがある場合は場合、は、新旧の値を返す新しい API を追加することを検討し、古い API は、古い値だけを返す継続を非推奨です。</span><span class="sxs-lookup"><span data-stu-id="b1601-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="b1601-158">既存のアプリケーションの互換性を維持するようになります。</span><span class="sxs-lookup"><span data-stu-id="b1601-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="b1601-159">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b1601-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b1601-160">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="b1601-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1601-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1601-161">See Also</span></span>  
 [<span data-ttu-id="b1601-162">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b1601-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="b1601-163">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b1601-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
