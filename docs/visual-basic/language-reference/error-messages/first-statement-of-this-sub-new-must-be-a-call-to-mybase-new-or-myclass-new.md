---
title: この最初のステートメント&#39;Sub New&#39;への呼び出しをする必要があります&#39;トラクター&#39;または&#39;'mybase.new'&#39; (No アクセス可能なコンス トラクター パラメーターのない)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589461"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="d0bfa-102">この最初のステートメント&#39;Sub New&#39;への呼び出しをする必要があります&#39;トラクター&#39;または&#39;'mybase.new'&#39; (No アクセス可能なコンス トラクター パラメーターのない)</span><span class="sxs-lookup"><span data-stu-id="d0bfa-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="d0bfa-103">この 'Sub New' の最初のステートメントが指定されて 'mybase.new' または 'myclass.new' への呼び出しをする必要があります基底クラス\<ベース名 >' の'\<derivedname >' は引数なしで呼び出せるアクセス可能な ' Sub New' がありません。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="d0bfa-104">派生クラスでは、すべてのコンス トラクターが基底クラスのコンス トラクターを呼び出す必要があります (`MyBase.New`)。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="d0bfa-105">基本クラスが派生クラスでアクセス可能なパラメーターなしのコンス トラクターを持つ場合`MyBase.New`自動的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="d0bfa-106">いない場合は、パラメーターを持つ基本クラスのコンス トラクターを呼び出す必要があり、自動的にこのことはできません。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="d0bfa-107">この場合、すべての派生クラスのコンス トラクターの最初のステートメントは、基本クラスでは、パラメーター化されたコンス トラクターを呼び出すか、呼び出す基底クラス コンス トラクターを派生クラスで別のコンス トラクターを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="d0bfa-108">**エラー ID:** BC30148</span><span class="sxs-lookup"><span data-stu-id="d0bfa-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0bfa-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="d0bfa-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d0bfa-110">呼び出すか`MyBase.New`必須のパラメーターを指定するか、このような呼び出しを行うピア コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="d0bfa-111">たとえば、基本クラスとして宣言されたコンス トラクターがある場合`Public Sub New(ByVal index as Integer)`、最初のステートメントで、派生クラスのコンス トラクターがあります`MyBase.New(100)`です。</span><span class="sxs-lookup"><span data-stu-id="d0bfa-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0bfa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0bfa-112">See Also</span></span>  
 [<span data-ttu-id="d0bfa-113">継承の基本</span><span class="sxs-lookup"><span data-stu-id="d0bfa-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
