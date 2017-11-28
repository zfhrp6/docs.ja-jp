---
title: "イベントとコールバック"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], extensibility
- methods [.NET Framework], callback
- callback methods
- callbacks
ms.assetid: 48b55c60-495f-4089-9396-97f9122bba7c
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 217e9eae3540e0a20afd0888d24803285d6352b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="events-and-callbacks"></a><span data-ttu-id="dcdd7-102">イベントとコールバック</span><span class="sxs-lookup"><span data-stu-id="dcdd7-102">Events and Callbacks</span></span>
<span data-ttu-id="dcdd7-103">コールバックでは、フレームワークがデリゲートからのユーザー コードにコールバックする機能拡張ポイントです。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-103">Callbacks are extensibility points that allow a framework to call back into user code through a delegate.</span></span> <span data-ttu-id="dcdd7-104">これらのデリゲートは、メソッドのパラメーターを通じて通常フレームワークに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-104">These delegates are usually passed to the framework through a parameter of a method.</span></span>  
  
 <span data-ttu-id="dcdd7-105">イベントは、デリゲート (イベント ハンドラー) を提供するための便利で一貫した構文をサポートするコールバックの特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-105">Events are a special case of callbacks that supports convenient and consistent syntax for supplying the delegate (an event handler).</span></span> <span data-ttu-id="dcdd7-106">さらに、Visual Studio のステートメント入力候補およびデザイナーは、イベント ベースの Api を使用してヘルプを提供します。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-106">In addition, Visual Studio’s statement completion and designers provide help in using event-based APIs.</span></span> <span data-ttu-id="dcdd7-107">(を参照してください[イベント デザイン](../../../docs/standard/design-guidelines/event.md))。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-107">(See [Event Design](../../../docs/standard/design-guidelines/event.md).)</span></span>  
  
 <span data-ttu-id="dcdd7-108">**✓ を検討してください**コールバックを使用して、フレームワークによって実行されるカスタム コードを提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-108">**✓ CONSIDER** using callbacks to allow users to provide custom code to be executed by the framework.</span></span>  
  
 <span data-ttu-id="dcdd7-109">**✓ を検討してください**イベントを使用したオブジェクト指向設計を理解することがなくてもフレームワークの動作をカスタマイズできるようにします。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-109">**✓ CONSIDER** using events to allow users to customize the behavior of a framework without the need for understanding object-oriented design.</span></span>  
  
 <span data-ttu-id="dcdd7-110">**✓ しないで**幅広い開発者になじみのあるは、ステートメント入力候補の Visual Studio と統合されたために、イベントを単純なコールバックよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-110">**✓ DO** prefer events over plain callbacks, because they are more familiar to a broader range of developers and are integrated with Visual Studio statement completion.</span></span>  
  
 <span data-ttu-id="dcdd7-111">**避け x**パフォーマンス重視の Api でのコールバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-111">**X AVOID** using callbacks in performance-sensitive APIs.</span></span>  
  
 <span data-ttu-id="dcdd7-112">**✓ は**新しい`Func<...>`、 `Action<...>`、または`Expression<...>`コールバックで Api を定義するときに、カスタム デリゲートではなく型です。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-112">**✓ DO** use the new `Func<...>`, `Action<...>`, or `Expression<...>` types instead of custom delegates, when defining APIs with callbacks.</span></span>  
  
 <span data-ttu-id="dcdd7-113">`Func<...>`および`Action<...>`汎用デリゲートを表します。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-113">`Func<...>` and `Action<...>` represent generic delegates.</span></span> <span data-ttu-id="dcdd7-114">`Expression<...>`コンパイルと、その後もできますが、実行時に呼び出されることができますを表す関数定義シリアル化およびリモート プロセスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-114">`Expression<...>` represents function definitions that can be compiled and subsequently invoked at runtime but can also be serialized and passed to remote processes.</span></span>  
  
 <span data-ttu-id="dcdd7-115">**✓ しないで**を測定しを使用するパフォーマンスの影響について理解する`Expression<...>`、使用する代わりに`Func<...>`と`Action<...>`デリゲート。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-115">**✓ DO** measure and understand performance implications of using `Expression<...>`, instead of using `Func<...>` and `Action<...>` delegates.</span></span>  
  
 <span data-ttu-id="dcdd7-116">`Expression<...>`型はほとんどの場合と論理的に等価に`Func<...>`と`Action<...>`デリゲート。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-116">`Expression<...>` types are in most cases logically equivalent to `Func<...>` and `Action<...>` delegates.</span></span> <span data-ttu-id="dcdd7-117">主な違いは、デリゲートがローカル処理のシナリオで使用するものでは、式がある場合と役に立つとリモート プロセスまたはコンピューターで式を評価することを意図しています。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-117">The main difference between them is that the delegates are intended to be used in local process scenarios; expressions are intended for cases where it’s beneficial and possible to evaluate the expression in a remote process or machine.</span></span>  
  
 <span data-ttu-id="dcdd7-118">**✓ しないで**するデリゲートを呼び出すことによって実行している任意のコードを理解し、セキュリティ、正確性、および互換性への影響を与える可能性です。</span><span class="sxs-lookup"><span data-stu-id="dcdd7-118">**✓ DO** understand that by calling a delegate, you are executing arbitrary code and that could have security, correctness, and compatibility repercussions.</span></span>  
  
 <span data-ttu-id="dcdd7-119">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="dcdd7-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="dcdd7-120">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="dcdd7-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdd7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcdd7-121">See Also</span></span>  
 [<span data-ttu-id="dcdd7-122">機能拡張のための設計</span><span class="sxs-lookup"><span data-stu-id="dcdd7-122">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="dcdd7-123">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="dcdd7-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
