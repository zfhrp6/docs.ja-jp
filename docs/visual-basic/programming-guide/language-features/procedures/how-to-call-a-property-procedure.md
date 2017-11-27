---
title: "方法: プロパティ プロシージャを呼び出す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="d1f60-102">方法: プロパティ プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d1f60-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="d1f60-103">プロパティ プロシージャを呼び出すには、「プロパティ値を格納するか値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="d1f60-104">プロパティは、変数にアクセスする同じ方法でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d1f60-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="d1f60-105">プロパティの`Set`プロシージャは値を格納して、その`Get`プロシージャが値を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="d1f60-106">ただし、明示的に呼び出さないこれらのプロシージャ名でします。</span><span class="sxs-lookup"><span data-stu-id="d1f60-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="d1f60-107">格納したり、変数の値を取得すると同様に、代入ステートメントまたは式のプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="d1f60-108">プロパティのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="d1f60-109">プロパティの Get プロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="d1f60-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="d1f60-110">式の中で変数名を使用するのと同様に対応するプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="d1f60-111">プロパティを使用する変数または定数を使用する任意の場所。</span><span class="sxs-lookup"><span data-stu-id="d1f60-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="d1f60-112">または</span><span class="sxs-lookup"><span data-stu-id="d1f60-112">-or-</span></span>  
  
     <span data-ttu-id="d1f60-113">等号の後、プロパティ名を使用して (`=`) 代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="d1f60-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="d1f60-114">次の例の値を読み取ります、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>プロパティ、暗黙的に呼び出してその`Get`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d1f60-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="d1f60-115">プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。</span><span class="sxs-lookup"><span data-stu-id="d1f60-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d1f60-116">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="d1f60-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="d1f60-117">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d1f60-118">プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="d1f60-119">プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1f60-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="d1f60-120">プロパティを呼び出すための手順を設定します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="d1f60-121">代入ステートメントの左側にあるプロパティの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="d1f60-122">次の例の値の設定、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>プロパティ、暗黙的に呼び出して、`Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="d1f60-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="d1f60-123">プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。</span><span class="sxs-lookup"><span data-stu-id="d1f60-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d1f60-124">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="d1f60-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="d1f60-125">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d1f60-126">プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="d1f60-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="d1f60-127">代入ステートメントの右側にある生成された値は、プロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d1f60-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1f60-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1f60-128">See Also</span></span>  
 [<span data-ttu-id="d1f60-129">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="d1f60-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="d1f60-130">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="d1f60-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d1f60-131">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="d1f60-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="d1f60-132">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="d1f60-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="d1f60-133">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="d1f60-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="d1f60-134">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="d1f60-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="d1f60-135">方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="d1f60-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="d1f60-136">方法 : プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="d1f60-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="d1f60-137">方法 : プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="d1f60-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="d1f60-138">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="d1f60-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="d1f60-139">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="d1f60-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
