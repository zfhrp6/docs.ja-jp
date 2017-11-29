---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="9e01b-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e01b-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="9e01b-103">1 つまたは複数の宣言されたプログラミング要素が、独自のクラス内または派生クラスからのみからアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e01b-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e01b-104">コメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-104">Remarks</span></span>  
 <span data-ttu-id="9e01b-105">クラスで宣言されたプログラミング要素が機密データまたは制限付きのコードを格納することもありますし、要素へのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="9e01b-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="9e01b-106">ただし、クラスが継承可能、派生クラスの階層が予想される場合は、これらの派生クラスのデータまたはコードにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e01b-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="9e01b-107">このような場合は、要素は、基本クラスとすべての派生クラスの両方にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="9e01b-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="9e01b-108">このような要素へのアクセスを制限するために宣言できます`Protected`です。</span><span class="sxs-lookup"><span data-stu-id="9e01b-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9e01b-109">ルール</span><span class="sxs-lookup"><span data-stu-id="9e01b-109">Rules</span></span>  
  
-   <span data-ttu-id="9e01b-110">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="9e01b-110">**Declaration Context.**</span></span> <span data-ttu-id="9e01b-111">使用することができます`Protected`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="9e01b-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="9e01b-112">つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9e01b-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="9e01b-113">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="9e01b-113">**Combined Modifiers.**</span></span> <span data-ttu-id="9e01b-114">使用することができます、`Protected`修飾子と共に、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)同じ宣言内での修飾子です。</span><span class="sxs-lookup"><span data-stu-id="9e01b-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="9e01b-115">この組み合わせでは、宣言された要素を独自のクラスおよび派生クラスからは、同じアセンブリに任意の場所からアクセス可能にします。</span><span class="sxs-lookup"><span data-stu-id="9e01b-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="9e01b-116">指定できます`Protected Friend`クラスのメンバーでのみです。</span><span class="sxs-lookup"><span data-stu-id="9e01b-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9e01b-117">動作</span><span class="sxs-lookup"><span data-stu-id="9e01b-117">Behavior</span></span>  
  
-   <span data-ttu-id="9e01b-118">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="9e01b-118">**Access Level.**</span></span> <span data-ttu-id="9e01b-119">クラスのすべてのコードは、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9e01b-119">All code in a class can access its elements.</span></span> <span data-ttu-id="9e01b-120">基本クラスから派生したクラス内のコードはすべてにアクセスできる、`Protected`基底クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="9e01b-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="9e01b-121">これは、派生のすべてのジェネレーションの場合は true です。</span><span class="sxs-lookup"><span data-stu-id="9e01b-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="9e01b-122">つまり、クラスにアクセスできるように`Protected`と基本クラスの基底クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="9e01b-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="9e01b-123">保護されたアクセスは、スーパー セットであるかのフレンド アクセスのサブセットではありません。</span><span class="sxs-lookup"><span data-stu-id="9e01b-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="9e01b-124">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="9e01b-124">**Access Modifiers.**</span></span> <span data-ttu-id="9e01b-125">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="9e01b-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="9e01b-126">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="9e01b-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9e01b-127">`Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e01b-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9e01b-128">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="9e01b-129">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="9e01b-130">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9e01b-131">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="9e01b-132">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9e01b-133">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="9e01b-134">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9e01b-135">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9e01b-136">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="9e01b-137">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9e01b-138">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="9e01b-139">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="9e01b-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e01b-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e01b-140">See Also</span></span>  
 [<span data-ttu-id="9e01b-141">Public</span><span class="sxs-lookup"><span data-stu-id="9e01b-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="9e01b-142">Friend</span><span class="sxs-lookup"><span data-stu-id="9e01b-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="9e01b-143">Private</span><span class="sxs-lookup"><span data-stu-id="9e01b-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="9e01b-144">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="9e01b-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="9e01b-145">手順</span><span class="sxs-lookup"><span data-stu-id="9e01b-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="9e01b-146">構造体</span><span class="sxs-lookup"><span data-stu-id="9e01b-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="9e01b-147">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="9e01b-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
