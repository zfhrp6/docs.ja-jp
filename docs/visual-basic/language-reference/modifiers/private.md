---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="6c21f-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c21f-102">Private (Visual Basic)</span></span>
<span data-ttu-id="6c21f-103">1 つまたは複数の宣言されたプログラミング要素がすべて含まれている型内からなど、宣言のコンテキストからのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c21f-104">コメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-104">Remarks</span></span>  
 <span data-ttu-id="6c21f-105">プログラミング要素は、独自の機能または機密データを含む、通常する場合、できるだけ厳密にへのアクセスを制限します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="6c21f-106">最大の制限は、モジュール、クラス、またはそれへのアクセスを定義する構造体のみを許可することで実現します。</span><span class="sxs-lookup"><span data-stu-id="6c21f-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="6c21f-107">この方法で要素へのアクセスを制限するために宣言できます`Private`です。</span><span class="sxs-lookup"><span data-stu-id="6c21f-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6c21f-108">ルール</span><span class="sxs-lookup"><span data-stu-id="6c21f-108">Rules</span></span>  
  
-   <span data-ttu-id="6c21f-109">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="6c21f-109">**Declaration Context.**</span></span> <span data-ttu-id="6c21f-110">`Private` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="6c21f-111">つまりの宣言コンテキスト、`Private`要素は、モジュール、クラス、または構造体にある必要があるあり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6c21f-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6c21f-112">動作</span><span class="sxs-lookup"><span data-stu-id="6c21f-112">Behavior</span></span>  
  
-   <span data-ttu-id="6c21f-113">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="6c21f-113">**Access Level.**</span></span> <span data-ttu-id="6c21f-114">宣言コンテキスト内のすべてのコードがアクセスできる、`Private`要素。</span><span class="sxs-lookup"><span data-stu-id="6c21f-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="6c21f-115">これには、入れ子になったクラスまたは列挙型の代入式などの包含の種類の中でコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="6c21f-116">宣言コンテキスト以外のコードからもアクセスできない、`Private`要素。</span><span class="sxs-lookup"><span data-stu-id="6c21f-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="6c21f-117">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="6c21f-117">**Access Modifiers.**</span></span> <span data-ttu-id="6c21f-118">アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。</span><span class="sxs-lookup"><span data-stu-id="6c21f-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6c21f-119">アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="6c21f-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="6c21f-120">`Private` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6c21f-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6c21f-121">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6c21f-122">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6c21f-123">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6c21f-124">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6c21f-125">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6c21f-126">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6c21f-127">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6c21f-128">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6c21f-129">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6c21f-130">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6c21f-131">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6c21f-132">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="6c21f-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6c21f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c21f-133">See Also</span></span>  
 [<span data-ttu-id="6c21f-134">Public</span><span class="sxs-lookup"><span data-stu-id="6c21f-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="6c21f-135">Protected</span><span class="sxs-lookup"><span data-stu-id="6c21f-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="6c21f-136">Friend</span><span class="sxs-lookup"><span data-stu-id="6c21f-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="6c21f-137">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="6c21f-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="6c21f-138">手順</span><span class="sxs-lookup"><span data-stu-id="6c21f-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="6c21f-139">構造体</span><span class="sxs-lookup"><span data-stu-id="6c21f-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6c21f-140">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="6c21f-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
