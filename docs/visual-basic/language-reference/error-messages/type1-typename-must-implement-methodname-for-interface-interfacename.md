---
title: '&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;methodname&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="bd4fb-102">&lt;type1&gt;&#39;&lt;typename&gt; &#39;実装する必要があります&#39; &lt;methodname&gt; &#39;インターフェイスの&#39; &lt;interfacename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="bd4fb-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="bd4fb-103">クラスまたは構造体、インターフェイスを実装する要求が、インターフェイスによって定義されたプロシージャは実装されません。</span><span class="sxs-lookup"><span data-stu-id="bd4fb-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="bd4fb-104">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd4fb-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="bd4fb-105">**エラー ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="bd4fb-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bd4fb-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bd4fb-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="bd4fb-107">同じ名前と、インターフェイスで定義されているシグネチャを持つプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="bd4fb-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="bd4fb-108">含めることを確認するには、少なくとも、`End Function`または`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="bd4fb-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="bd4fb-109">追加、`Implements`句の末尾に、`Function`または`Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="bd4fb-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="bd4fb-110">例えば:</span><span class="sxs-lookup"><span data-stu-id="bd4fb-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bd4fb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd4fb-111">See Also</span></span>  
 [<span data-ttu-id="bd4fb-112">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="bd4fb-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="bd4fb-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bd4fb-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
