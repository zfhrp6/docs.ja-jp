---
title: '&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;methodname&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="320f8-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;methodname&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="320f8-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;methodname&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="320f8-103">クラスまたは構造体、インターフェイスを実装する要求が、インターフェイスによって定義されたプロシージャは実装されません。</span><span class="sxs-lookup"><span data-stu-id="320f8-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="320f8-104">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="320f8-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="320f8-105">**エラー ID:** BC30149</span><span class="sxs-lookup"><span data-stu-id="320f8-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="320f8-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="320f8-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="320f8-107">同じ名前と、インターフェイスで定義されているシグネチャを持つプロシージャを宣言します。</span><span class="sxs-lookup"><span data-stu-id="320f8-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="320f8-108">含めることを確認するには、少なくとも、`End Function`または`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="320f8-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="320f8-109">追加、`Implements`句の末尾に、`Function`または`Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="320f8-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="320f8-110">例:</span><span class="sxs-lookup"><span data-stu-id="320f8-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="320f8-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="320f8-111">See Also</span></span>  
 [<span data-ttu-id="320f8-112">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="320f8-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="320f8-113">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="320f8-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
