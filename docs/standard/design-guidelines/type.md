---
title: "型のデザインのガイドライン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6b02abef0180b6de82e26837863849cce35c994f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="type-design-guidelines"></a><span data-ttu-id="47199-102">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="47199-102">Type Design Guidelines</span></span>
<span data-ttu-id="47199-103">CLR の観点からは、型の 2 つのカテゴリがあります: 参照型と値の型: フレームワーク デザインの詳細については、するためにお種類以上の論理グループ分け、それぞれ独自の特定のデザイン規則には。</span><span class="sxs-lookup"><span data-stu-id="47199-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="47199-104">クラスは、参照型の一般的なケースです。</span><span class="sxs-lookup"><span data-stu-id="47199-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="47199-105">ほとんどのフレームワークの型の大部分を構成します。</span><span class="sxs-lookup"><span data-stu-id="47199-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="47199-106">クラスは、豊富なサポートされるオブジェクト指向の機能の設定と、一般的な適用性、人気を支払わなかったです。</span><span class="sxs-lookup"><span data-stu-id="47199-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="47199-107">基本クラスと抽象クラスは、拡張機能に関連する特殊な論理グループです。</span><span class="sxs-lookup"><span data-stu-id="47199-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="47199-108">インターフェイスは、参照型と値の型の両方によって実装可能な型の型です。</span><span class="sxs-lookup"><span data-stu-id="47199-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="47199-109">したがって、参照型と値の型のポリモーフィックな階層のルートとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="47199-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="47199-110">さらに、インターフェイスを使用して、CLR によってネイティブにサポートされていない複数の継承をシミュレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="47199-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="47199-111">構造体は、値型の一般的なケースがあり、小規模で単純な種類、言語プリミティブのような用に予約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47199-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="47199-112">列挙型は、日、週、コンソールの色、およびなどのような値の短いセットを定義するために使用する値型の特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="47199-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="47199-113">静的クラスは、静的メンバーのコンテナーを目的としての種類です。</span><span class="sxs-lookup"><span data-stu-id="47199-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="47199-114">その他の操作へのショートカットを提供するよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="47199-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="47199-115">デリゲート、例外、属性、配列、およびコレクションは、特別な用途のためのもので、参照型のすべての特殊なケースであり、設計と使用法についてのガイドラインがこのドキュメントで部分で説明されています。</span><span class="sxs-lookup"><span data-stu-id="47199-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="47199-116">**✓ しないで**各型が適切に定義された一連の関連するメンバーは、関連付けられていない機能のランダムなコレクションだけでなくであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47199-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47199-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="47199-117">In This Section</span></span>  
 [<span data-ttu-id="47199-118">クラスまたは構造体の選択</span><span class="sxs-lookup"><span data-stu-id="47199-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="47199-119">抽象クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="47199-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="47199-120">静的クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="47199-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="47199-121">インターフェイスのデザイン</span><span class="sxs-lookup"><span data-stu-id="47199-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="47199-122">構造体のデザイン</span><span class="sxs-lookup"><span data-stu-id="47199-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="47199-123">列挙型デザイン</span><span class="sxs-lookup"><span data-stu-id="47199-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="47199-124">入れ子にされた型</span><span class="sxs-lookup"><span data-stu-id="47199-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="47199-125">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="47199-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="47199-126">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="47199-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47199-127">参照</span><span class="sxs-lookup"><span data-stu-id="47199-127">See Also</span></span>  
 [<span data-ttu-id="47199-128">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="47199-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
