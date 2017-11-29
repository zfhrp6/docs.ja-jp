---
title: "例外のスロー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b1aa0eaccc26e1bd7cc6b78953dc0a782b2f952e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="exception-throwing"></a><span data-ttu-id="50722-102">例外のスロー</span><span class="sxs-lookup"><span data-stu-id="50722-102">Exception Throwing</span></span>
<span data-ttu-id="50722-103">このセクションで説明されている例外スローのガイドラインでは、実行エラーの意味を適切な定義が必要です。</span><span class="sxs-lookup"><span data-stu-id="50722-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="50722-104">メンバーが実行できないときに実行エラーが発生する (新機能、メンバー名のとおり) を実行するように設計します。</span><span class="sxs-lookup"><span data-stu-id="50722-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="50722-105">たとえば場合、`OpenFile`メソッドは、呼び出し元に、開いているファイル ハンドルを返すことはできません、実行エラーと見なされるとします。</span><span class="sxs-lookup"><span data-stu-id="50722-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="50722-106">ほとんどの開発者は、0 または null 参照による除算などの使用状況のエラーの例外の使用に慣れてになっています。</span><span class="sxs-lookup"><span data-stu-id="50722-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="50722-107">Framework では、例外は、実行エラーを含む、すべてのエラー条件に使用されます。</span><span class="sxs-lookup"><span data-stu-id="50722-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="50722-108">**X しないで**エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="50722-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="50722-109">例外は、フレームワークにエラーを報告の主な手段です。</span><span class="sxs-lookup"><span data-stu-id="50722-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="50722-110">**✓ しないで**例外をスローして、実行の失敗を報告します。</span><span class="sxs-lookup"><span data-stu-id="50722-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="50722-111">**✓ を検討してください**呼び出すことによって、プロセスを終了して`System.Environment.FailFast`(.NET Framework 2.0 の機能)、コードが安全に実行をさらにはない状況が発生すると、例外をスローする代わりにします。</span><span class="sxs-lookup"><span data-stu-id="50722-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="50722-112">**X しないで**可能であれば、コントロールの通常のフローの例外を使用します。</span><span class="sxs-lookup"><span data-stu-id="50722-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="50722-113">システム障害、潜在的な競合状態を持つ操作を除くユーザーが例外をスローしないコードを記述できるように、フレームワークの設計者は Api を設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50722-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="50722-114">たとえば、ユーザーが例外をスローしないコードを記述できるようにメンバーを呼び出す前に前提条件を確認する方法を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="50722-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="50722-115">別のメンバーの前提条件の確認に使用するメンバーは多くの場合と呼ばれ、テスト担当者を実際に実行するメンバーは、渡ってと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="50722-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="50722-116">場合、テスト担当者渡ってパターンが許容できないパフォーマンス オーバーヘッドを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="50722-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="50722-117">このような場合、いわゆる Try 解析パターン見なす必要があります (を参照してください[例外とパフォーマンス](../../../docs/standard/design-guidelines/exceptions-and-performance.md)詳細については)。</span><span class="sxs-lookup"><span data-stu-id="50722-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="50722-118">**✓ を検討してください**パフォーマンス上の違いの例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="50722-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="50722-119">1 秒あたり 100 を超える throw レートは、ほとんどのアプリケーションのパフォーマンスに著しい影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="50722-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="50722-120">**✓ しないで**ドキュメントによって公開されている呼び出し可能なメンバー、メンバーの違反のためにスローされる例外すべてではなく、システム障害) コントラクトおよびコントラクトの一部として扱われるようにします。</span><span class="sxs-lookup"><span data-stu-id="50722-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="50722-121">コントラクトの一部である例外は、次に 1 つのバージョンから変更しないでください (つまり、例外の種類を変更しないでください、および新しい例外を追加してはならない)。</span><span class="sxs-lookup"><span data-stu-id="50722-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="50722-122">**X しないで**かどうか throw をできるパブリック メンバーに基づいてにいくつかのオプションです。</span><span class="sxs-lookup"><span data-stu-id="50722-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="50722-123">**X しないで**パブリック メンバーの戻り値として例外を返すをまたは`out`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="50722-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="50722-124">それらをスローする代わりにパブリック Api から例外を返す例外ベースのエラー報告の利点の多くを無効にします。</span><span class="sxs-lookup"><span data-stu-id="50722-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="50722-125">**✓ を検討してください**例外ビルダー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="50722-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="50722-126">一般的な場所から同じ例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="50722-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="50722-127">コードの肥大化を回避するのには、例外を作成し、それらのプロパティを初期化するヘルパー メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="50722-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="50722-128">また、例外をスローするメンバーが取得されないインライン展開されます。</span><span class="sxs-lookup"><span data-stu-id="50722-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="50722-129">Throw ステートメント ビルダー内を移動すると、インライン展開を解除するメンバーことができます。</span><span class="sxs-lookup"><span data-stu-id="50722-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="50722-130">**X しないで**例外フィルター ブロックから例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="50722-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="50722-131">例外フィルターには、例外が発生したときに、CLR で例外をキャッチし、フィルターが false を返します。</span><span class="sxs-lookup"><span data-stu-id="50722-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="50722-132">この動作を実行して、明示的に false を返すフィルターから区別することであり、デバッグが非常に困難であるためです。</span><span class="sxs-lookup"><span data-stu-id="50722-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="50722-133">**避け x**明示的に finally ブロックからの例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="50722-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="50722-134">暗黙的にスローされたによってスローされる例外をスローするメソッドを呼び出すことは可能です。</span><span class="sxs-lookup"><span data-stu-id="50722-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="50722-135">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="50722-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="50722-136">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="50722-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50722-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="50722-137">See Also</span></span>  
 [<span data-ttu-id="50722-138">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="50722-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="50722-139">例外のデザイン ガイドライン</span><span class="sxs-lookup"><span data-stu-id="50722-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
