---
title: "&#39;です。&lt;typename&gt;&#39; から継承できません&lt;型&gt;&#39;&lt; 。basetypename&gt;&#39;ベースのアクセスを展開しているためです&lt;型&gt;、アセンブリ外。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords: BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="d8f2a-102">&#39;です。&lt;typename&gt;&#39; から継承できません&lt;型&gt;&#39;&lt; 。basetypename&gt;&#39;ベースのアクセスを展開しているためです&lt;型&gt;、アセンブリ外。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="d8f2a-103">基本クラスからクラスまたはインターフェイスを継承またはインターフェイスが、制限の緩いアクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="d8f2a-104">たとえば、`Public`インターフェイスから継承、`Friend`インターフェイス、または`Protected`クラスから継承、`Private`クラスです。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="d8f2a-105">これは、基底クラスまたは目的のレベル以外にアクセスするインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="d8f2a-106">**エラー ID:** BC30910</span><span class="sxs-lookup"><span data-stu-id="d8f2a-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d8f2a-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d8f2a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="d8f2a-108">派生クラスまたはインターフェイスには、少なくとも基底クラスまたはインターフェイスと同程度に制限を指定のアクセス レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="d8f2a-109">または</span><span class="sxs-lookup"><span data-stu-id="d8f2a-109">-or-</span></span>  
  
-   <span data-ttu-id="d8f2a-110">制限の緩いアクセス レベルを必要とする場合は、削除、`Inherits`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="d8f2a-111">さらに制限された基底クラスまたはインターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="d8f2a-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f2a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8f2a-112">See Also</span></span>  
 [<span data-ttu-id="d8f2a-113">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="d8f2a-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="d8f2a-114">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="d8f2a-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="d8f2a-115">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="d8f2a-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="d8f2a-116">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="d8f2a-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
