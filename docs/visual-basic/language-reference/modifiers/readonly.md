---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a><span data-ttu-id="46573-102">ReadOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46573-102">ReadOnly (Visual Basic)</span></span>
<span data-ttu-id="46573-103">変数またはプロパティを読み取るがある書き込まれませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="46573-103">Specifies that a variable or property can be read but not written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46573-104">コメント</span><span class="sxs-lookup"><span data-stu-id="46573-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="46573-105">ルール</span><span class="sxs-lookup"><span data-stu-id="46573-105">Rules</span></span>  
  
-   <span data-ttu-id="46573-106">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="46573-106">**Declaration Context.**</span></span> <span data-ttu-id="46573-107">`ReadOnly` は、モジュール レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="46573-107">You can use `ReadOnly` only at module level.</span></span> <span data-ttu-id="46573-108">つまりの宣言コンテキスト、`ReadOnly`要素は、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="46573-108">This means the declaration context for a `ReadOnly` element must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="46573-109">**結合された修飾子。**</span><span class="sxs-lookup"><span data-stu-id="46573-109">**Combined Modifiers.**</span></span> <span data-ttu-id="46573-110">指定することはできません`ReadOnly`と共に`Static`同じ宣言内で。</span><span class="sxs-lookup"><span data-stu-id="46573-110">You cannot specify `ReadOnly` together with `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="46573-111">**値を代入しています。**</span><span class="sxs-lookup"><span data-stu-id="46573-111">**Assigning a Value.**</span></span> <span data-ttu-id="46573-112">コードの使用、`ReadOnly`プロパティは、その値を設定できません。</span><span class="sxs-lookup"><span data-stu-id="46573-112">Code consuming a `ReadOnly` property cannot set its value.</span></span> <span data-ttu-id="46573-113">基になる記憶域にアクセスするコードが割り当てるまたはいつでも、値を変更します。</span><span class="sxs-lookup"><span data-stu-id="46573-113">But code that has access to the underlying storage can assign or change the value at any time.</span></span>  
  
     <span data-ttu-id="46573-114">値を割り当てることができます、`ReadOnly`変数の宣言またはクラスまたは定義されている構造体のコンス トラクターでのみです。</span><span class="sxs-lookup"><span data-stu-id="46573-114">You can assign a value to a `ReadOnly` variable only in its declaration or in the constructor of a class or structure in which it is defined.</span></span>  
  
## <a name="when-to-use-a-readonly-variable"></a><span data-ttu-id="46573-115">読み取り専用変数を使用する場合</span><span class="sxs-lookup"><span data-stu-id="46573-115">When to Use a ReadOnly Variable</span></span>  
 <span data-ttu-id="46573-116">使用することはできませんが、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)を宣言し、定数値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="46573-116">There are situations in which you cannot use a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value.</span></span> <span data-ttu-id="46573-117">たとえば、`Const`ステートメントで割り当てるには、必要なデータ型を受け入れない場合や、定数式でのコンパイル時に値を計算することができません。</span><span class="sxs-lookup"><span data-stu-id="46573-117">For example, the `Const` statement might not accept the data type you want to assign, or you might not be able to compute the value at compile time with a constant expression.</span></span> <span data-ttu-id="46573-118">わからない場合がありますも値コンパイル時にします。</span><span class="sxs-lookup"><span data-stu-id="46573-118">You might not even know the value at compile time.</span></span> <span data-ttu-id="46573-119">このような場合は、使用することができます、`ReadOnly`定数値を保持する変数。</span><span class="sxs-lookup"><span data-stu-id="46573-119">In these cases, you can use a `ReadOnly` variable to hold a constant value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="46573-120">場合でも、変数自体に、そのメンバーを変更することができます、変数のデータ型が配列またはクラスのインスタンスなど、参照型の場合`ReadOnly`です。</span><span class="sxs-lookup"><span data-stu-id="46573-120">If the data type of the variable is a reference type, such as an array or a class instance, its members can be changed even if the variable itself is `ReadOnly`.</span></span> <span data-ttu-id="46573-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="46573-121">The following example illustrates this.</span></span>  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 <span data-ttu-id="46573-122">初期化する場合、配列を指す`characterArray()`を保持"x"、"y"および"z"です。</span><span class="sxs-lookup"><span data-stu-id="46573-122">When initialized, the array pointed to by `characterArray()` holds "x", "y", and "z".</span></span> <span data-ttu-id="46573-123">変数`characterArray`は`ReadOnly`、初期化; であると、その値を変更することはできません、新しい配列を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="46573-123">Because the variable `characterArray` is `ReadOnly`, you cannot change its value once it is initialized; that is, you cannot assign a new array to it.</span></span> <span data-ttu-id="46573-124">ただし、配列メンバーの 1 つ以上の値を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="46573-124">However, you can change the values of one or more of the array members.</span></span> <span data-ttu-id="46573-125">次のプロシージャの呼び出し`changeArrayElement`、配列を指す`characterArray()`を保持"x"、"M"および"z"です。</span><span class="sxs-lookup"><span data-stu-id="46573-125">Following a call to the procedure `changeArrayElement`, the array pointed to by `characterArray()` holds "x", "M", and "z".</span></span>  
  
 <span data-ttu-id="46573-126">これは、プロシージャ パラメーターの宣言に似て[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)プロシージャが呼び出し元引数自体を変更できないようにするが、そのメンバーを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="46573-126">Note that this is similar to declaring a procedure parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md), which prevents the procedure from changing the calling argument itself but allows it to change its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46573-127">例</span><span class="sxs-lookup"><span data-stu-id="46573-127">Example</span></span>  
 <span data-ttu-id="46573-128">次の例では定義、`ReadOnly`従業員が雇用された日付のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="46573-128">The following example defines a `ReadOnly` property for the date on which an employee was hired.</span></span> <span data-ttu-id="46573-129">プロパティ値としての内部クラス ストア、`Private`クラス内の変数、およびのみのコードは、その値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="46573-129">The class stores the property value internally as a `Private` variable, and only code inside the class can change that value.</span></span> <span data-ttu-id="46573-130">ただし、このプロパティは`Public`、すべてのコードをクラスにアクセスできますが、プロパティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="46573-130">However, the property is `Public`, and any code that can access the class can read the property.</span></span>  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 <span data-ttu-id="46573-131">`ReadOnly` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="46573-131">The `ReadOnly` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="46573-132">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="46573-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="46573-133">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="46573-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="46573-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="46573-134">See Also</span></span>  
 [<span data-ttu-id="46573-135">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="46573-135">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="46573-136">キーワード</span><span class="sxs-lookup"><span data-stu-id="46573-136">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
