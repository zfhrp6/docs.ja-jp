---
title: "Implements 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="75850-102">Implements 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75850-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="75850-103">クラスまたは構造体のメンバーがインターフェイスで定義されているメンバーの実装を提供していることを示します。</span><span class="sxs-lookup"><span data-stu-id="75850-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75850-104">コメント</span><span class="sxs-lookup"><span data-stu-id="75850-104">Remarks</span></span>  
<span data-ttu-id="75850-105">`Implements`キーワードと同じではない、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="75850-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="75850-106">使用する、`Implements`クラスまたは構造体は、1 つまたは複数のインターフェイスを実装して、各メンバーを使用することを指定するステートメント、`Implements`どのインターフェイスとメンバーを指定するキーワードを実装します。</span><span class="sxs-lookup"><span data-stu-id="75850-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="75850-107">クラスまたは構造体、インターフェイスを実装する場合は含める必要があります、`Implements`ステートメントの直後に、[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)または[Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)、およびすべてのメンバーを実装する必要がありますインターフェイスによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="75850-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="75850-108">再実装が必要</span><span class="sxs-lookup"><span data-stu-id="75850-108">Reimplementation</span></span>  
<span data-ttu-id="75850-109">派生クラスでは、基本クラスが実装済みインターフェイスのメンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="75850-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="75850-110">これは、次の点で基底クラスのメンバーをオーバーライドすると異なります。</span><span class="sxs-lookup"><span data-stu-id="75850-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="75850-111">基底クラスのメンバーがする必要がない[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)実装するためにします。</span><span class="sxs-lookup"><span data-stu-id="75850-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="75850-112">別の名前を持つメンバーを再実装できます。</span><span class="sxs-lookup"><span data-stu-id="75850-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="75850-113">`Implements`キーワードは、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="75850-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="75850-114">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="75850-115">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="75850-116">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="75850-117">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="75850-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="75850-118">See Also</span></span>  
 [<span data-ttu-id="75850-119">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="75850-120">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="75850-121">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="75850-122">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="75850-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
