---
title: Set ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604836"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="6f8b5-102">Set ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f8b5-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="6f8b5-103">宣言、`Set`プロパティ プロシージャのプロパティに値を代入するために使用します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f8b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f8b5-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="6f8b5-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="6f8b5-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="6f8b5-106">任意。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-106">Optional.</span></span> <span data-ttu-id="6f8b5-107">参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="6f8b5-108">1 つの省略可能な`Get`と`Set`このプロパティ内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="6f8b5-109">次のいずれかの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="6f8b5-110">Protected</span><span class="sxs-lookup"><span data-stu-id="6f8b5-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="6f8b5-111">Friend</span><span class="sxs-lookup"><span data-stu-id="6f8b5-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="6f8b5-112">Private</span><span class="sxs-lookup"><span data-stu-id="6f8b5-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="6f8b5-113">参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="6f8b5-114">必須。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-114">Required.</span></span> <span data-ttu-id="6f8b5-115">プロパティの新しい値を格納するパラメーター。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="6f8b5-116">場合は必須`Option Strict`は`On`します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="6f8b5-117">データ型、`value`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="6f8b5-118">指定されたデータ型は、プロパティのデータ型と同じである必要があります、これ`Set`ステートメントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="6f8b5-119">任意。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-119">Optional.</span></span> <span data-ttu-id="6f8b5-120">場合に実行する 1 つまたは複数のステートメント、`Set`プロパティ プロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="6f8b5-121">必須。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-121">Required.</span></span> <span data-ttu-id="6f8b5-122">定義を終了、`Set`プロパティ プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f8b5-123">コメント</span><span class="sxs-lookup"><span data-stu-id="6f8b5-123">Remarks</span></span>  
 <span data-ttu-id="6f8b5-124">すべてのプロパティがあります、`Set`プロパティ プロシージャ、プロパティが設定されていない限り`ReadOnly`です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="6f8b5-125">`Set`プロパティの値を設定する手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="6f8b5-126">Visual Basic は、このプロパティの自動的に呼び出します`Set`代入ステートメントは、プロパティに格納される値を提供するときの手順です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="6f8b5-127">Visual Basic のパラメーターを渡す、`Set`プロパティの割り当て時にプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="6f8b5-128">パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="6f8b5-129">パラメーターでは、プロパティに割り当てられる値を保持します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="6f8b5-130">通常プライベート ローカル変数にこの値を格納して返すたびに、`Get`プロシージャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="6f8b5-131">プロパティの宣言の本体でのみ、プロパティを含めることができます`Get`と`Set`間でのプロシージャ、 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="6f8b5-132">これらのプロシージャ以外のものを格納できません。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="6f8b5-133">具体的には、プロパティの現在の値を格納できません。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="6f8b5-134">プロパティ プロシージャのいずれかの内側で保存する場合、その他のプロパティ プロシージャ アクセスできないために、プロパティの外部には、この値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="6f8b5-135">通常の方法は、の値を格納する、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと同じレベルで宣言された変数です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="6f8b5-136">定義する必要があります、`Set`に適用すると、プロパティの内部プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="6f8b5-137">`Set`プロシージャの既定値は、包含するプロパティのアクセス レベルを使用する場合を除き、`accessmodifier`で、`Set`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6f8b5-138">ルール</span><span class="sxs-lookup"><span data-stu-id="6f8b5-138">Rules</span></span>  
  
-   <span data-ttu-id="6f8b5-139">**混合アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="6f8b5-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="6f8b5-140">必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`プロシージャが、両方は使用できません。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="6f8b5-141">これを行うと、プロシージャのアクセス レベルがプロパティのアクセス レベルよりも制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="6f8b5-142">プロパティが宣言されている場合など、 `Friend`、宣言することができます、`Set`プロシージャ`Private`、ではなく`Public`です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="6f8b5-143">定義する場合、 `WriteOnly` 、プロパティ、`Set`プロシージャが全体のプロパティを表します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="6f8b5-144">レベルを別のアクセスを宣言することはできません`Set`プロパティの 2 つのアクセス レベルを設定することがあるため、します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6f8b5-145">動作</span><span class="sxs-lookup"><span data-stu-id="6f8b5-145">Behavior</span></span>  
  
-   <span data-ttu-id="6f8b5-146">**プロパティ プロシージャから取得します。**</span><span class="sxs-lookup"><span data-stu-id="6f8b5-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="6f8b5-147">ときに、`Set`次のステートメントを格納する値が指定されている、プロシージャ呼び出し元のコードに戻ると、実行が継続します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="6f8b5-148">`Set` プロパティ プロシージャは、いずれかを使用して返すことができます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)または[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="6f8b5-149">`Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="6f8b5-150">任意の数の`Exit Property`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Property`と`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f8b5-151">例</span><span class="sxs-lookup"><span data-stu-id="6f8b5-151">Example</span></span>  
 <span data-ttu-id="6f8b5-152">次の例では、`Set`プロパティの値を設定するステートメント。</span><span class="sxs-lookup"><span data-stu-id="6f8b5-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6f8b5-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f8b5-153">See Also</span></span>  
 [<span data-ttu-id="6f8b5-154">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="6f8b5-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="6f8b5-155">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="6f8b5-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="6f8b5-156">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="6f8b5-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="6f8b5-157">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="6f8b5-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
