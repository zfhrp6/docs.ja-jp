---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="public-visual-basic"></a><span data-ttu-id="b7228-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7228-102">Public (Visual Basic)</span></span>
<span data-ttu-id="b7228-103">1 つまたは複数の宣言されたプログラミング要素にアクセス制限がありますいないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7228-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7228-104">コメント</span><span class="sxs-lookup"><span data-stu-id="b7228-104">Remarks</span></span>  
 <span data-ttu-id="b7228-105">コンポーネントまたはクラス ライブラリなどのコンポーネントのセットを公開している場合は、プログラミング要素へのアセンブリと相互運用する任意のコードからアクセスできる通常します。</span><span class="sxs-lookup"><span data-stu-id="b7228-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="b7228-106">このような要素に無制限のアクセスを与えるには、ことを宣言できます`Public`です。</span><span class="sxs-lookup"><span data-stu-id="b7228-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="b7228-107">パブリック アクセスへのアクセスを制限する必要がないときに、プログラミング要素には、通常のレベルです。</span><span class="sxs-lookup"><span data-stu-id="b7228-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="b7228-108">要素のアクセス レベルがインターフェイス、モジュール、クラスまたは構造体内で宣言されていることに注意してください。 既定値は`Public`特に宣言しない場合。</span><span class="sxs-lookup"><span data-stu-id="b7228-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b7228-109">ルール</span><span class="sxs-lookup"><span data-stu-id="b7228-109">Rules</span></span>  
  
-   <span data-ttu-id="b7228-110">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="b7228-110">**Declaration Context.**</span></span> <span data-ttu-id="b7228-111">使用することができます`Public`モジュール、インターフェイス、または名前空間レベルでのみです。</span><span class="sxs-lookup"><span data-stu-id="b7228-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="b7228-112">つまりの宣言コンテキスト、`Public`要素は、ソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体にある必要があるあり、プロシージャをすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b7228-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b7228-113">動作</span><span class="sxs-lookup"><span data-stu-id="b7228-113">Behavior</span></span>  
  
-   <span data-ttu-id="b7228-114">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="b7228-114">**Access Level.**</span></span> <span data-ttu-id="b7228-115">モジュール、クラスまたは構造体にアクセスできるすべてのコードがアクセスできる、`Public`要素。</span><span class="sxs-lookup"><span data-stu-id="b7228-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="b7228-116">**既定のアクセス。**</span><span class="sxs-lookup"><span data-stu-id="b7228-116">**Default Access.**</span></span> <span data-ttu-id="b7228-117">パブリック アクセスを既定のプロシージャ内のローカル変数は、それらのアクセス修飾子を使用できません。</span><span class="sxs-lookup"><span data-stu-id="b7228-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="b7228-118">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="b7228-118">**Access Modifiers.**</span></span> <span data-ttu-id="b7228-119">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="b7228-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="b7228-120">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="b7228-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="b7228-121">`Public` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7228-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="b7228-122">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="b7228-123">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="b7228-124">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="b7228-125">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="b7228-126">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="b7228-127">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="b7228-128">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="b7228-129">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b7228-130">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="b7228-131">Module ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="b7228-132">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="b7228-133">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b7228-134">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="b7228-135">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="b7228-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b7228-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7228-136">See Also</span></span>  
 [<span data-ttu-id="b7228-137">Protected</span><span class="sxs-lookup"><span data-stu-id="b7228-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="b7228-138">Friend</span><span class="sxs-lookup"><span data-stu-id="b7228-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="b7228-139">Private</span><span class="sxs-lookup"><span data-stu-id="b7228-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="b7228-140">[保護されたプライベート](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="b7228-140">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="b7228-141">[保護されたフレンド](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="b7228-141">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="b7228-142">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b7228-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="b7228-143">手順</span><span class="sxs-lookup"><span data-stu-id="b7228-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="b7228-144">構造体</span><span class="sxs-lookup"><span data-stu-id="b7228-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="b7228-145">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="b7228-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
