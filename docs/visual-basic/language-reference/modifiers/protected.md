---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="protected-visual-basic"></a><span data-ttu-id="e5859-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5859-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="e5859-103">1 つまたは複数のプログラミング要素が宣言されていることを指定するメンバーのアクセス修飾子は、独自のクラス内または派生クラスからからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e5859-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5859-104">コメント</span><span class="sxs-lookup"><span data-stu-id="e5859-104">Remarks</span></span>  
 <span data-ttu-id="e5859-105">クラスで宣言されたプログラミング要素が機密データまたは制限付きのコードを格納することもありますし、要素へのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="e5859-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="e5859-106">ただし、クラスが継承可能、派生クラスの階層が予想される場合は、これらの派生クラスのデータまたはコードにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5859-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="e5859-107">このような場合は、要素は、基本クラスとすべての派生クラスの両方にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="e5859-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="e5859-108">このような要素へのアクセスを制限するために宣言できます`Protected`です。</span><span class="sxs-lookup"><span data-stu-id="e5859-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="e5859-109">`Protected`アクセス修飾子は、その他の 2 つの修飾子と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="e5859-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="e5859-110">[Protected Friend](protected-friend.md)修飾子は、クラス メンバーをそのクラスの派生クラスからそのクラスが定義されている同じアセンブリ内からアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="e5859-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="e5859-111">[プライベート保護](private-protected.md)修飾子により、クラス メンバー アクセス、含んでいるアセンブリ内でのみ、派生型です。</span><span class="sxs-lookup"><span data-stu-id="e5859-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="e5859-112">ルール</span><span class="sxs-lookup"><span data-stu-id="e5859-112">Rules</span></span>  
  
-   <span data-ttu-id="e5859-113">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="e5859-113">**Declaration Context.**</span></span> <span data-ttu-id="e5859-114">使用することができます`Protected`クラス レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="e5859-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="e5859-115">つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e5859-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="e5859-116">動作</span><span class="sxs-lookup"><span data-stu-id="e5859-116">Behavior</span></span>  
  
-   <span data-ttu-id="e5859-117">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="e5859-117">**Access Level.**</span></span> <span data-ttu-id="e5859-118">クラスのすべてのコードは、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e5859-118">All code in a class can access its elements.</span></span> <span data-ttu-id="e5859-119">基本クラスから派生したクラス内のコードはすべてにアクセスできる、`Protected`基底クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="e5859-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="e5859-120">これは、派生のすべてのジェネレーションの場合は true です。</span><span class="sxs-lookup"><span data-stu-id="e5859-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="e5859-121">つまり、クラスにアクセスできるように`Protected`と基本クラスの基底クラスの要素。</span><span class="sxs-lookup"><span data-stu-id="e5859-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="e5859-122">保護されたアクセスは、スーパー セットであるかのフレンド アクセスのサブセットではありません。</span><span class="sxs-lookup"><span data-stu-id="e5859-122">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="e5859-123">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="e5859-123">**Access Modifiers.**</span></span> <span data-ttu-id="e5859-124">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="e5859-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="e5859-125">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="e5859-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="e5859-126">`Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e5859-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e5859-127">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e5859-128">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="e5859-129">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="e5859-130">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e5859-131">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="e5859-132">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="e5859-133">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="e5859-134">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e5859-135">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e5859-136">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e5859-137">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e5859-138">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="e5859-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5859-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5859-139">See Also</span></span>  
 [<span data-ttu-id="e5859-140">Public</span><span class="sxs-lookup"><span data-stu-id="e5859-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="e5859-141">Friend</span><span class="sxs-lookup"><span data-stu-id="e5859-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="e5859-142">Private</span><span class="sxs-lookup"><span data-stu-id="e5859-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="e5859-143">[保護されたプライベート](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="e5859-143">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="e5859-144">[保護されたフレンド](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="e5859-144">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="e5859-145">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="e5859-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="e5859-146">手順</span><span class="sxs-lookup"><span data-stu-id="e5859-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="e5859-147">構造体</span><span class="sxs-lookup"><span data-stu-id="e5859-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e5859-148">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e5859-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
