---
title: "&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;membername&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords: BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a><span data-ttu-id="d6e7e-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; する必要があります実装 &#39;&lt;membername&gt;&#39; インターフェイス &#39;&lt;interfacename&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-102">&lt;type1&gt;&#39;&lt;typename&gt;&#39; must implement &#39;&lt;membername&gt;&#39; for interface &#39;&lt;interfacename&gt;&#39;</span></span>
<span data-ttu-id="d6e7e-103">'\<typename >' を実装する必要があります'\<membername >' のインターフェイス '\<interfacename >' です。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-103">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="d6e7e-104">プロパティを実装する必要があります一致する 'ReadOnly' または 'WriteOnly' 指定子。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-104">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>  
  
 <span data-ttu-id="d6e7e-105">クラスまたは構造体、インターフェイスを実装する要求が、プロシージャ、プロパティ、またはインターフェイスで定義されたイベントは実装されません。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-105">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="d6e7e-106">インターフェイスのすべてのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-106">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="d6e7e-107">**エラー ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="d6e7e-107">**Error ID:** BC30154</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6e7e-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d6e7e-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="d6e7e-109">同じ名前と、インターフェイスで定義されているシグネチャを持つメンバーを宣言します。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-109">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="d6e7e-110">含めることを確認するには、少なくとも、 `End Function`、 `End Sub`、または`End Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-110">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="d6e7e-111">追加、`Implements`句の末尾に、 `Function`、 `Sub`、 `Property`、または`Event`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-111">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="d6e7e-112">例:</span><span class="sxs-lookup"><span data-stu-id="d6e7e-112">For example:</span></span>  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  <span data-ttu-id="d6e7e-113">プロパティを実装するときに、以下のことを確認`ReadOnly`または`WriteOnly`は、インターフェイス定義の場合と同じ方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-113">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>  
  
4.  <span data-ttu-id="d6e7e-114">プロパティを実装する場合は、宣言`Get`と`Set`プロシージャに、必要に応じて。</span><span class="sxs-lookup"><span data-stu-id="d6e7e-114">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e7e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6e7e-115">See Also</span></span>  
 [<span data-ttu-id="d6e7e-116">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="d6e7e-116">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="d6e7e-117">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6e7e-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
