---
title: 演算子のオーバーロード
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 747fc21aceae60e362c72391ae265e45d6f8445f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="operator-overloads"></a><span data-ttu-id="3db4f-102">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="3db4f-102">Operator Overloads</span></span>
<span data-ttu-id="3db4f-103">演算子のオーバー ロードは、framework の型をした組み込みの言語プリミティブを表示を許可します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="3db4f-104">許可されている、いくつかの状況で役に立ちますが、演算子のオーバー ロードを慎重に使用してください。</span><span class="sxs-lookup"><span data-stu-id="3db4f-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="3db4f-105">演算子のオーバー ロードがされて悪用などの単純なメソッドにする必要のある操作で演算子を使用するフレームワークの設計者が開始されたときに多くの場合があります。</span><span class="sxs-lookup"><span data-stu-id="3db4f-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="3db4f-106">次のガイドラインには、演算子のオーバー ロードを使用するタイミングと方法を決定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3db4f-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="3db4f-107">**避け x**を除く演算子のオーバー ロードを定義する必要があります (組み込み) のプリミティブ型と感じての種類でします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="3db4f-108">**✓ を検討してください**演算子のオーバー ロードを定義する型がプリミティブ型のように感じる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3db4f-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="3db4f-109">たとえば、<xref:System.String?displayProperty=nameWithType>が`operator==`と`operator!=`定義します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="3db4f-110">**✓ しないで**番号を表す構造体で演算子オーバー ロードを定義する (など<xref:System.Decimal?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="3db4f-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="3db4f-111">**X しないで**演算子のオーバー ロードを定義するときに分別して使用します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="3db4f-112">演算子のオーバー ロードが簡単にすぐに操作の結果がどうなる場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="3db4f-113">1 を減算できる理にかなってなど<xref:System.DateTime>別の`DateTime`を取得し、<xref:System.TimeSpan>です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="3db4f-114">ただしが適切でない共用体の 2 つのデータベース クエリでは、論理、union 演算子を使用するか、ストリームに書き込むシフト演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="3db4f-115">**X しないで**オーバー ロードを定義する型のオペランドの少なくとも 1 つがない限り、演算子がオーバー ロードを提供します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="3db4f-116">**✓ しないで**対称的に演算子をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="3db4f-117">たとえば、オーバー ロードする場合、`operator==`もオーバー ロードする必要がある、`operator!=`です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="3db4f-118">同様に、オーバー ロードする場合、`operator<`もオーバー ロードする必要がある、`operator>`のようにします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="3db4f-119">**✓ を検討してください**各オーバー ロードされた演算子に対応するフレンドリ名を持つメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="3db4f-120">多くの言語は、演算子のオーバー ロードをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3db4f-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="3db4f-121">このため、演算子をオーバー ロードする型が、同等の機能は、適切なドメイン固有の名前を持つセカンダリ メソッドを含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="3db4f-122">次の表には、演算子と、対応するわかりやすいメソッド名の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3db4f-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="3db4f-123">C# 演算子記号</span><span class="sxs-lookup"><span data-stu-id="3db4f-123">C# Operator Symbol</span></span>|<span data-ttu-id="3db4f-124">メタデータ名</span><span class="sxs-lookup"><span data-stu-id="3db4f-124">Metadata Name</span></span>|<span data-ttu-id="3db4f-125">フレンドリ名</span><span class="sxs-lookup"><span data-stu-id="3db4f-125">Friendly Name</span></span>|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a><span data-ttu-id="3db4f-126">演算子をオーバー ロード = =</span><span class="sxs-lookup"><span data-stu-id="3db4f-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="3db4f-127">オーバー ロード`operator ==`はかなり複雑になります。</span><span class="sxs-lookup"><span data-stu-id="3db4f-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="3db4f-128">演算子のセマンティクスをなどの他のいくつかのメンバーと互換性がある必要があります<xref:System.Object.Equals%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="3db4f-129">変換演算子</span><span class="sxs-lookup"><span data-stu-id="3db4f-129">Conversion Operators</span></span>  
 <span data-ttu-id="3db4f-130">変換演算子は、単項演算子を別の型に変換できるようにします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="3db4f-131">演算子は、オペランドまたは戻り値の型のいずれかの静的メンバーとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3db4f-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="3db4f-132">変換演算子の 2 種類があります。 明示的および暗黙的なです。</span><span class="sxs-lookup"><span data-stu-id="3db4f-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="3db4f-133">**X しないで**エンドユーザーでこのような変換が明確に予期されていない場合は、変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="3db4f-134">**X しないで**型のドメインの外部の変換演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="3db4f-135">たとえば、 <xref:System.Int32>、 <xref:System.Double>、および<xref:System.Decimal>はのすべての数値型に対し<xref:System.DateTime>はありません。</span><span class="sxs-lookup"><span data-stu-id="3db4f-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="3db4f-136">したがって、存在しないはず変換演算子に変換する、`Double(long)`を`DateTime`です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="3db4f-137">コンス トラクターは、このような場合が優先されます。</span><span class="sxs-lookup"><span data-stu-id="3db4f-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="3db4f-138">**X しないで**変換が損失を伴う可能性がある場合は、暗黙的な変換演算子を提供します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="3db4f-139">たとえば、存在することはできませんから暗黙的な変換`Double`に`Int32`ため`Double`よりも広い範囲を持つ`Int32`します。</span><span class="sxs-lookup"><span data-stu-id="3db4f-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="3db4f-140">変換が損失を伴う可能性がある場合でも、明示的な変換演算子を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3db4f-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="3db4f-141">**X しないで**暗黙的なキャストから例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3db4f-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="3db4f-142">エンドユーザーがないかもしれません変換が行われているために、何が起こっているかを理解するため非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="3db4f-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="3db4f-143">**✓ しないで**スロー<xref:System.InvalidCastException?displayProperty=nameWithType>でキャスト演算子への呼び出しが損失を伴う変換と演算子のコントラクトでは、非可逆の変換は許可されません。</span><span class="sxs-lookup"><span data-stu-id="3db4f-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="3db4f-144">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3db4f-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3db4f-145">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="3db4f-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db4f-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="3db4f-146">See Also</span></span>  
 [<span data-ttu-id="3db4f-147">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3db4f-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="3db4f-148">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="3db4f-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
