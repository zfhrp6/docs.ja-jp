---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="private-visual-basic"></a><span data-ttu-id="bbdcb-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bbdcb-102">Private (Visual Basic)</span></span>
<span data-ttu-id="bbdcb-103">1 つまたは複数の宣言されたプログラミング要素がすべて含まれている型内からなど、宣言のコンテキストからのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbdcb-104">コメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-104">Remarks</span></span>  
 <span data-ttu-id="bbdcb-105">プログラミング要素は、独自の機能または機密データを含む、通常する場合、できるだけ厳密にへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="bbdcb-106">最大の制限は、モジュール、クラス、またはそれへのアクセスを定義する構造体のみを許可することで実現します。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="bbdcb-107">この方法で要素へのアクセスを制限するために宣言できます`Private`です。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="bbdcb-108">使用することも、[プライベート保護](private-protected.md)メンバーにそのクラス内、および、含んでいるアセンブリにある派生クラスからアクセスできるよう、アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="bbdcb-109">ルール</span><span class="sxs-lookup"><span data-stu-id="bbdcb-109">Rules</span></span>  

-   <span data-ttu-id="bbdcb-110">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="bbdcb-110">**Declaration Context.**</span></span> <span data-ttu-id="bbdcb-111">`Private` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="bbdcb-112">つまりの宣言コンテキスト、`Private`要素は、モジュール、クラス、または構造体にある必要があるあり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bbdcb-113">動作</span><span class="sxs-lookup"><span data-stu-id="bbdcb-113">Behavior</span></span>  
  
-   <span data-ttu-id="bbdcb-114">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="bbdcb-114">**Access Level.**</span></span> <span data-ttu-id="bbdcb-115">宣言コンテキスト内のすべてのコードがアクセスできる、`Private`要素。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="bbdcb-116">これには、入れ子になったクラスまたは列挙型の代入式などの包含の種類の中でコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="bbdcb-117">宣言コンテキスト以外のコードからもアクセスできない、`Private`要素。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="bbdcb-118">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="bbdcb-118">**Access Modifiers.**</span></span> <span data-ttu-id="bbdcb-119">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="bbdcb-120">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="bbdcb-121">`Private` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbdcb-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bbdcb-122">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="bbdcb-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="bbdcb-124">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="bbdcb-125">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="bbdcb-126">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="bbdcb-127">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="bbdcb-128">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="bbdcb-129">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bbdcb-130">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="bbdcb-131">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bbdcb-132">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="bbdcb-133">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="bbdcb-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bbdcb-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbdcb-134">See Also</span></span>  
 [<span data-ttu-id="bbdcb-135">Public</span><span class="sxs-lookup"><span data-stu-id="bbdcb-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="bbdcb-136">Protected</span><span class="sxs-lookup"><span data-stu-id="bbdcb-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="bbdcb-137">Friend</span><span class="sxs-lookup"><span data-stu-id="bbdcb-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="bbdcb-138">[保護されたプライベート](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="bbdcb-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="bbdcb-139">[Protected Friend](./protected-friend.md)[Visual Basic でのレベルのアクセス    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="bbdcb-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="bbdcb-140">手順</span><span class="sxs-lookup"><span data-stu-id="bbdcb-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="bbdcb-141">構造体</span><span class="sxs-lookup"><span data-stu-id="bbdcb-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="bbdcb-142">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="bbdcb-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
