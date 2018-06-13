---
title: '&#39;&lt;typename&gt; &#39;から継承できません&lt;型&gt; &#39; &lt;basetypename&gt; &#39;ベースのアクセスを展開しているため&lt;型&gt;。アセンブリの外部'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598425"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="5ada2-102">&#39;&lt;typename&gt; &#39;から継承できません&lt;型&gt; &#39; &lt;basetypename&gt; &#39;ベースのアクセスを展開しているため&lt;型&gt;。アセンブリの外部</span><span class="sxs-lookup"><span data-stu-id="5ada2-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="5ada2-103">基本クラスからクラスまたはインターフェイスを継承またはインターフェイスが、制限の緩いアクセス レベル。</span><span class="sxs-lookup"><span data-stu-id="5ada2-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="5ada2-104">たとえば、`Public`インターフェイスから継承、`Friend`インターフェイス、または`Protected`クラスから継承、`Private`クラスです。</span><span class="sxs-lookup"><span data-stu-id="5ada2-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="5ada2-105">これは、基底クラスまたは目的のレベル以外にアクセスするインターフェイスを公開します。</span><span class="sxs-lookup"><span data-stu-id="5ada2-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="5ada2-106">**エラー ID:** BC30910</span><span class="sxs-lookup"><span data-stu-id="5ada2-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ada2-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5ada2-107">To correct this error</span></span>  
  
-   <span data-ttu-id="5ada2-108">派生クラスまたはインターフェイスには、少なくとも基底クラスまたはインターフェイスと同程度に制限を指定のアクセス レベルを変更します。</span><span class="sxs-lookup"><span data-stu-id="5ada2-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="5ada2-109">- または -</span><span class="sxs-lookup"><span data-stu-id="5ada2-109">-or-</span></span>  
  
-   <span data-ttu-id="5ada2-110">制限の緩いアクセス レベルを必要とする場合は、削除、`Inherits`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="5ada2-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="5ada2-111">さらに制限された基底クラスまたはインターフェイスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="5ada2-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ada2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ada2-112">See Also</span></span>  
 [<span data-ttu-id="5ada2-113">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="5ada2-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="5ada2-114">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="5ada2-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="5ada2-115">Inherits ステートメント</span><span class="sxs-lookup"><span data-stu-id="5ada2-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="5ada2-116">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="5ada2-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
