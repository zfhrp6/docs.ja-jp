---
title: 等値演算子
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1e5784de277d59c7bc945cbe7b605653eec7bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="equality-operators"></a><span data-ttu-id="800e1-102">等値演算子</span><span class="sxs-lookup"><span data-stu-id="800e1-102">Equality Operators</span></span>
<span data-ttu-id="800e1-103">このセクションでは、オーバー ロードの等値演算子について説明しを指す`operator==`と`operator!=`等値演算子として。</span><span class="sxs-lookup"><span data-stu-id="800e1-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="800e1-104">**X しないで**等値演算子および以外のいずれかのオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="800e1-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="800e1-105">**✓ しないで**いることを確認<xref:System.Object.Equals%2A?displayProperty=nameWithType>等値演算子は、同じセマンティクスと同様のパフォーマンス特性があるとします。</span><span class="sxs-lookup"><span data-stu-id="800e1-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="800e1-106">多くの場合、つまり`Object.Equals`等値演算子はオーバー ロード時に上書きする必要があります。</span><span class="sxs-lookup"><span data-stu-id="800e1-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="800e1-107">**避け x**等値演算子から例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="800e1-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="800e1-108">たとえば、引数のいずれかがスローする代わりに null の場合は false を返す`NullReferenceException`です。</span><span class="sxs-lookup"><span data-stu-id="800e1-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="800e1-109">値型で等値演算子</span><span class="sxs-lookup"><span data-stu-id="800e1-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="800e1-110">**✓ しないで**等しいかどうかがわかりやすい場合は、値型で等値演算子をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="800e1-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="800e1-111">ほとんどのプログラミング言語での既定の実装はありません`operator==`値型です。</span><span class="sxs-lookup"><span data-stu-id="800e1-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="800e1-112">参照型で等値演算子</span><span class="sxs-lookup"><span data-stu-id="800e1-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="800e1-113">**避け x**変更可能な参照型で等値演算子のオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="800e1-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="800e1-114">多くの言語では、参照型の組み込みの等値演算子があります。</span><span class="sxs-lookup"><span data-stu-id="800e1-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="800e1-115">組み込み演算子は通常の参照の等価性を実装し、値の等価性を既定の動作が変更されたときに、多くの開発者は驚くします。</span><span class="sxs-lookup"><span data-stu-id="800e1-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="800e1-116">不変より参照の等価性と値の等価性の間の違いに注意をはるかに困難になるために、変更できない参照型のこの問題が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="800e1-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="800e1-117">**避け x**実装では、参照の等価性の場合よりもはるかに低速になる場合は、参照型で等値演算子をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="800e1-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="800e1-118">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="800e1-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="800e1-119">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="800e1-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800e1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="800e1-120">See Also</span></span>  
 [<span data-ttu-id="800e1-121">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="800e1-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="800e1-122">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="800e1-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
