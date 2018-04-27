---
title: メンバーのデザインのガイドライン
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f4e33735a934b1ac41c34ccb9698c172ada28e1
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="member-design-guidelines"></a><span data-ttu-id="98a12-102">メンバーのデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="98a12-102">Member Design Guidelines</span></span>
<span data-ttu-id="98a12-103">メソッド、プロパティ、イベント、コンス トラクター、およびフィールドは、メンバーとしてまとめて呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="98a12-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="98a12-104">メンバーは、最終的に、フレームワークのエンドユーザーに、フレームワークの機能が公開されている手段です。</span><span class="sxs-lookup"><span data-stu-id="98a12-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="98a12-105">メンバーは、仮想または非仮想、具象か抽象クラスで静的メソッドまたはインスタンスを指定でき、ユーザー補助機能のいくつかの異なるスコープを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="98a12-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="98a12-106">このすべてのさまざまな驚異的な表現力には、同時に、フレームワーク デザイナー部分注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="98a12-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="98a12-107">この章では、任意の型のメンバーをデザインするときに従う必要がありますの基本的なガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="98a12-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98a12-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="98a12-108">In This Section</span></span>  
 [<span data-ttu-id="98a12-109">メンバーのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="98a12-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="98a12-110">プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="98a12-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="98a12-111">コンストラクターのデザイン</span><span class="sxs-lookup"><span data-stu-id="98a12-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="98a12-112">イベントのデザイン</span><span class="sxs-lookup"><span data-stu-id="98a12-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="98a12-113">フィールドのデザイン</span><span class="sxs-lookup"><span data-stu-id="98a12-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="98a12-114">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="98a12-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="98a12-115">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="98a12-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="98a12-116">パラメーターのデザイン</span><span class="sxs-lookup"><span data-stu-id="98a12-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="98a12-117">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="98a12-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="98a12-118">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="98a12-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a12-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="98a12-119">See Also</span></span>  
 [<span data-ttu-id="98a12-120">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="98a12-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
