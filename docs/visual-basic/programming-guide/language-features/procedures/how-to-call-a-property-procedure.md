---
title: "方法: プロパティ プロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d0d37fc2b7ae1d563a7e9d0a8e75343dd690089b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="17dd1-102">方法: プロパティ プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17dd1-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="17dd1-103">プロパティ プロシージャを呼び出すには、「プロパティに値を格納するかの値を取得しますします。</span><span class="sxs-lookup"><span data-stu-id="17dd1-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="17dd1-104">プロパティは変数にアクセスする同じ方法でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="17dd1-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="17dd1-105">プロパティの`Set`プロシージャは、値を格納し、その`Get`プロシージャが値を取得します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="17dd1-106">ただし、明示的に呼び出さないこれらのプロシージャ名。</span><span class="sxs-lookup"><span data-stu-id="17dd1-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="17dd1-107">格納および変数の値を取得すると同様に、代入ステートメント、または式でプロパティを使用するとします。</span><span class="sxs-lookup"><span data-stu-id="17dd1-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="17dd1-108">プロパティのプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="17dd1-109">プロパティの Get プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="17dd1-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="17dd1-110">式の中で変数名を使用すると同じように対応するプロパティ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="17dd1-111">プロパティを使用する変数または定数を使用する任意の場所。</span><span class="sxs-lookup"><span data-stu-id="17dd1-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="17dd1-112">または</span><span class="sxs-lookup"><span data-stu-id="17dd1-112">-or-</span></span>  
  
     <span data-ttu-id="17dd1-113">後に続くプロパティ名を使用して (`=`)、代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="17dd1-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="17dd1-114">次の例は、値を読み取って、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>プロパティには、暗黙的に呼び出すことの`Get`プロシージャ</xref:Microsoft.VisualBasic.DateAndTime.Now%2A>。</span><span class="sxs-lookup"><span data-stu-id="17dd1-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="17dd1-115">[!code-vb[VbVbalrDateProperties&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="17dd1-115">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="17dd1-116">プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。</span><span class="sxs-lookup"><span data-stu-id="17dd1-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="17dd1-117">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="17dd1-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="17dd1-118">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="17dd1-119">プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="17dd1-120">プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="17dd1-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="17dd1-121">プロパティを呼び出すための手順を設定します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-121">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="17dd1-122">代入ステートメントの左側にあるプロパティの名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="17dd1-123">次の例の値の設定、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>プロパティには、暗黙的に呼び出す、`Set`プロシージャ</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>。</span><span class="sxs-lookup"><span data-stu-id="17dd1-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     <span data-ttu-id="17dd1-124">[!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="17dd1-124">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span></span>  
  
2.  <span data-ttu-id="17dd1-125">プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。</span><span class="sxs-lookup"><span data-stu-id="17dd1-125">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="17dd1-126">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="17dd1-126">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="17dd1-127">コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-127">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="17dd1-128">プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。</span><span class="sxs-lookup"><span data-stu-id="17dd1-128">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="17dd1-129">代入ステートメントの右側にある生成された値は、このプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="17dd1-129">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17dd1-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="17dd1-130">See Also</span></span>  
 <span data-ttu-id="17dd1-131">[プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-131">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="17dd1-132"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="17dd1-133"> [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-133"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="17dd1-134"> [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-134"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="17dd1-135"> [方法: プロパティを作成します。](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-135"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="17dd1-136"> [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-136"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="17dd1-137"> [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-137"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="17dd1-138"> [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-138"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="17dd1-139"> [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-139"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md) </span></span>  
<span data-ttu-id="17dd1-140"> [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="17dd1-140"> [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="17dd1-141"> [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="17dd1-141"> [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
