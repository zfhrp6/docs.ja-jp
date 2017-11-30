---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 32f993e4b9bcd126ebb6d70310fc0781e8b137b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="e6674-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6674-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="e6674-103">1 つまたは複数の宣言されたプログラミング要素がその宣言を含むアセンブリ内からのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6674-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6674-104">コメント</span><span class="sxs-lookup"><span data-stu-id="e6674-104">Remarks</span></span>  
 <span data-ttu-id="e6674-105">多くの場合、クラスと構造体を宣言しているコンポーネントがだけでなく、アセンブリ全体で使用するなどの要素をプログラミングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="e6674-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="e6674-106">ただしに (たとえば、アプリケーションは商標で守ら) 場合、アセンブリの外部コードによってアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6674-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="e6674-107">この方法で要素へのアクセスを制限する場合は、使用して宣言できます、`Friend`修飾子です。</span><span class="sxs-lookup"><span data-stu-id="e6674-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="e6674-108">その他のクラス、構造体、およびコンパイルされますが、同じモジュールのコード アセンブリはすべてにアクセスできる、`Friend`そのアセンブリ内の要素。</span><span class="sxs-lookup"><span data-stu-id="e6674-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="e6674-109">`Friend`アクセスは、アプリケーションのプログラミング要素に望ましいレベルでは多くの場合と`Friend`インターフェイス、モジュール、クラスまたは構造のレベルで既定のアクセス。</span><span class="sxs-lookup"><span data-stu-id="e6674-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="e6674-110">使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="e6674-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="e6674-111">したがって、宣言コンテキスト、`Friend`ソース ファイル、名前空間、インターフェイス、モジュール、クラスまたは構造体を要素として使用することがあります。 プロシージャをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e6674-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="e6674-112">使用することができます、`Friend`修飾子と共に、 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)同じ宣言内での修飾子です。</span><span class="sxs-lookup"><span data-stu-id="e6674-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="e6674-113">この組み合わせを設定すると、両方とも`Friend`アクセスと保護されたアクセスで宣言された要素、および派生クラス独自のクラスからは、同じアセンブリに任意の場所からアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="e6674-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="e6674-114">指定できます`Protected Friend`クラスのメンバーでのみです。</span><span class="sxs-lookup"><span data-stu-id="e6674-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="e6674-115">比較について`Friend`と、その他のアクセス修飾子を参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="e6674-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e6674-116">別のアセンブリがで許可されているすべての種類およびとマークされているメンバーにアクセスするアセンブリを指定することができます`Friend`です。</span><span class="sxs-lookup"><span data-stu-id="e6674-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="e6674-117">詳細については、[Friend アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6674-117">For more information, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6674-118">例</span><span class="sxs-lookup"><span data-stu-id="e6674-118">Example</span></span>  
 <span data-ttu-id="e6674-119">次のクラスは、`Friend`特定のメンバーにアクセスする同じアセンブリ内の他のプログラミング要素を許可する修飾子です。</span><span class="sxs-lookup"><span data-stu-id="e6674-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="e6674-120">使用方法</span><span class="sxs-lookup"><span data-stu-id="e6674-120">Usage</span></span>  
 <span data-ttu-id="e6674-121">使用することができます、`Friend`これらのコンテキストで修飾子。</span><span class="sxs-lookup"><span data-stu-id="e6674-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="e6674-122">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="e6674-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="e6674-124">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="e6674-125">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="e6674-126">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="e6674-127">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="e6674-128">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="e6674-129">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="e6674-130">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="e6674-131">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="e6674-132">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="e6674-133">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="e6674-134">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="e6674-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e6674-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6674-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="e6674-136">Public</span><span class="sxs-lookup"><span data-stu-id="e6674-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="e6674-137">Protected</span><span class="sxs-lookup"><span data-stu-id="e6674-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="e6674-138">Private</span><span class="sxs-lookup"><span data-stu-id="e6674-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="e6674-139">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="e6674-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="e6674-140">手順</span><span class="sxs-lookup"><span data-stu-id="e6674-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="e6674-141">構造体</span><span class="sxs-lookup"><span data-stu-id="e6674-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="e6674-142">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e6674-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
