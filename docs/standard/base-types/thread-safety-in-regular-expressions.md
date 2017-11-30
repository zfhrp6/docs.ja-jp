---
title: "正規表現におけるスレッド セーフ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="bd74b-102">正規表現におけるスレッド セーフ</span><span class="sxs-lookup"><span data-stu-id="bd74b-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="bd74b-103"><xref:System.Text.RegularExpressions.Regex>クラス自体がスレッド セーフであり変更できない (読み取り専用で)。</span><span class="sxs-lookup"><span data-stu-id="bd74b-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="bd74b-104">つまり、**Regex** オブジェクトは任意のスレッドで作成できます。また、スレッド間で共有できます。一致するメソッドは任意のスレッドから呼び出すことができますが、グローバルな状態を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="bd74b-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="bd74b-105">ただし、結果オブジェクト (**一致**と**MatchCollection**) によって返される**Regex**シングル スレッド内で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd74b-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="bd74b-106">これらのオブジェクトの多くは、論理的に変更できませんが、実装によってパフォーマンスを改善するために一部の結果の演算を遅延させることができます。結果として、呼び出し側はオブジェクトに対するアクセスをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd74b-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="bd74b-107">複数のスレッドで **Regex** オブジェクトを共有する必要がある場合、同期されたメソッドを呼び出すことで、それらのオブジェクトはスレッドセーフ インスタンスに変換できます。</span><span class="sxs-lookup"><span data-stu-id="bd74b-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="bd74b-108">列挙子の例外はありますが、すべての正規表現クラスはスレッド セーフです。または、同期されたメソッドでスレッドセーフ オブジェクトに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="bd74b-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="bd74b-109">列挙子は唯一の例外です。</span><span class="sxs-lookup"><span data-stu-id="bd74b-109">Enumerators are the only exception.</span></span> <span data-ttu-id="bd74b-110">アプリケーションはコレクション列挙子に対する呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd74b-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="bd74b-111">複数のスレッドでコレクションを同時に列挙できる場合、列挙子によってスキャンされるコレクションのルート オブジェクト上の列挙子メソッドを同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd74b-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd74b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd74b-112">See Also</span></span>  
 [<span data-ttu-id="bd74b-113">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="bd74b-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
