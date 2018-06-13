---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234590"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="5d4f7-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d4f7-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="5d4f7-103">1 つまたは複数の宣言されたプログラミング要素がその宣言を含むアセンブリ内からのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d4f7-104">コメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-104">Remarks</span></span>  
 <span data-ttu-id="5d4f7-105">多くの場合、クラスと構造体を宣言しているコンポーネントがだけでなく、アセンブリ全体で使用するなどの要素をプログラミングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="5d4f7-106">ただしに (たとえば、アプリケーションは商標で守ら) 場合、アセンブリの外部コードによってアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="5d4f7-107">この方法で要素へのアクセスを制限する場合は、使用して宣言できます、`Friend`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="5d4f7-108">その他のクラス、構造体、およびコンパイルされますが、同じモジュールのコード アセンブリはすべてにアクセスできる、`Friend`そのアセンブリ内の要素。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="5d4f7-109">`Friend` アクセスは、アプリケーションのプログラミング要素に望ましいレベルでは多くの場合と`Friend`インターフェイス、モジュール、クラスまたは構造のレベルで既定のアクセス。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="5d4f7-110">使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="5d4f7-111">したがって、宣言コンテキスト、`Friend`ソース ファイル、名前空間、インターフェイス、モジュール、クラスまたは構造体を要素として使用することがあります。 プロシージャをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="5d4f7-112">使用することも、 [Protected Friend](protected-friend.md)アクセス修飾子は、クラス メンバーをそのクラスの派生クラスからそのクラスが定義されている同じアセンブリ内からアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="5d4f7-113">使用して、同じアセンブリ内の派生クラスからそのクラス内からのメンバーへのアクセスを制限する、[プライベート保護](private-protected.md)アクセス修飾子。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="5d4f7-114">比較について`Friend`と、その他のアクセス修飾子を参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d4f7-115">別のアセンブリがで許可されているすべての種類およびとマークされているメンバーにアクセスするアセンブリを指定することができます`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="5d4f7-116">詳細については、[Friend アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d4f7-117">例</span><span class="sxs-lookup"><span data-stu-id="5d4f7-117">Example</span></span>  
 <span data-ttu-id="5d4f7-118">次のクラスは、`Friend`特定のメンバーにアクセスする同じアセンブリ内の他のプログラミング要素を許可する修飾子です。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="5d4f7-119">使用法</span><span class="sxs-lookup"><span data-stu-id="5d4f7-119">Usage</span></span>  
 <span data-ttu-id="5d4f7-120">使用することができます、`Friend`これらのコンテキストで修飾子。</span><span class="sxs-lookup"><span data-stu-id="5d4f7-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="5d4f7-121">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="5d4f7-122">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="5d4f7-123">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="5d4f7-124">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="5d4f7-125">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5d4f7-126">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="5d4f7-127">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5d4f7-128">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5d4f7-129">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="5d4f7-130">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="5d4f7-131">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5d4f7-132">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="5d4f7-133">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="5d4f7-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5d4f7-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d4f7-134">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="5d4f7-135">Public</span><span class="sxs-lookup"><span data-stu-id="5d4f7-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="5d4f7-136">Protected</span><span class="sxs-lookup"><span data-stu-id="5d4f7-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="5d4f7-137">Private</span><span class="sxs-lookup"><span data-stu-id="5d4f7-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="5d4f7-138">[保護されたプライベート](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f7-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="5d4f7-139">[保護されたフレンド](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="5d4f7-139">[Protected Friend](./protected-friend.md) </span></span>  
 [<span data-ttu-id="5d4f7-140">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="5d4f7-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="5d4f7-141">手順</span><span class="sxs-lookup"><span data-stu-id="5d4f7-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="5d4f7-142">構造体</span><span class="sxs-lookup"><span data-stu-id="5d4f7-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5d4f7-143">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="5d4f7-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
