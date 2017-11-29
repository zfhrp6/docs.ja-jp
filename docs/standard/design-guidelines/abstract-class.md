---
title: "抽象クラスのデザイン"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="87cf4-102">抽象クラスのデザイン</span><span class="sxs-lookup"><span data-stu-id="87cf4-102">Abstract Class Design</span></span>
<span data-ttu-id="87cf4-103">**X しないで**抽象型の public または protected のコンス トラクター内部を定義します。</span><span class="sxs-lookup"><span data-stu-id="87cf4-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="87cf4-104">コンス トラクターは、ユーザーが型のインスタンスを作成する必要がある場合にのみ、パブリックにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87cf4-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="87cf4-105">抽象型のインスタンスを作成できないため、パブリック コンス トラクターを持つ抽象型が正しくされていない仕様であり、ユーザーに誤解を招く。</span><span class="sxs-lookup"><span data-stu-id="87cf4-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="87cf4-106">**✓ しないで**抽象クラス内で、保護されているか、内部のコンス トラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="87cf4-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="87cf4-107">プロテクト コンス トラクターより一般的なサブタイプが作成されるときに、独自の初期化を実行する基本クラスでは。</span><span class="sxs-lookup"><span data-stu-id="87cf4-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="87cf4-108">アセンブリのクラスを定義する抽象クラスの具象実装を制限する、内部のコンス トラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="87cf4-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="87cf4-109">**✓ しないで**を出荷する各の抽象クラスから継承する少なくとも 1 つの具象型を提供します。</span><span class="sxs-lookup"><span data-stu-id="87cf4-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="87cf4-110">抽象クラスの設計を検証するには、これによりを行っています。</span><span class="sxs-lookup"><span data-stu-id="87cf4-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="87cf4-111">たとえば、<xref:System.IO.FileStream?displayProperty=nameWithType>に実装されて、<xref:System.IO.Stream?displayProperty=nameWithType>抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="87cf4-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="87cf4-112">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="87cf4-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="87cf4-113">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="87cf4-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cf4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="87cf4-114">See Also</span></span>  
 [<span data-ttu-id="87cf4-115">型のデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="87cf4-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="87cf4-116">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="87cf4-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
