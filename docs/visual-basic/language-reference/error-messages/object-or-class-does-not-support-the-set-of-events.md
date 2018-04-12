---
title: オブジェクトまたはクラスがこのイベント セットをサポートしていません。
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="6843e-102">オブジェクトまたはクラスがこのイベント セットをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="6843e-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="6843e-103">使用して、`WithEvents`できない動作するように指定された一連のイベントのイベント ソース コンポーネントを含む変数。</span><span class="sxs-lookup"><span data-stu-id="6843e-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="6843e-104">オブジェクトのイベントをシンク、別のオブジェクトを作成したいなど`Implements`最初のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6843e-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="6843e-105">実装済みのオブジェクトからイベントをシンクすると思うかもしれませんが、これが一致しない場合です。</span><span class="sxs-lookup"><span data-stu-id="6843e-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="6843e-106">`Implements`メソッドとプロパティのインターフェイスを実装するだけです。</span><span class="sxs-lookup"><span data-stu-id="6843e-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="6843e-107">`WithEvents`プライベートはサポートされていません`UserControls`発生する種類の情報が必要なため、`ObjectEvent`実行時に使用できません。</span><span class="sxs-lookup"><span data-stu-id="6843e-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6843e-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6843e-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="6843e-109">元のイベントではないが、コンポーネントのイベントをシンクことはできません。</span><span class="sxs-lookup"><span data-stu-id="6843e-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6843e-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6843e-110">See Also</span></span>  
 [<span data-ttu-id="6843e-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="6843e-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="6843e-112">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="6843e-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
