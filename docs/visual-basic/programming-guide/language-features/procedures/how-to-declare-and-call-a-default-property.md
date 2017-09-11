---
title: "方法: 宣言し、Visual Basic では、既定のプロパティを呼び出して |Microsoft ドキュメント"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: 7cfd476def67ccf46e524da7943680f9e34b6a26
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="ae0ed-102">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae0ed-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="ae0ed-103">A*既定プロパティ*クラスまたは構造体のプロパティで、指定しなくても、コードにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="ae0ed-104">クラスまたは構造体がプロパティではなく、名前のコードを呼び出すと、コンテキスト プロパティへのアクセスを許可する[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]が存在する場合に、そのクラスまたは構造体の既定のプロパティにアクセスを解決します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-104">When calling code names a class or structure but not a property, and the context allows access to a property, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="ae0ed-105">クラスまたは構造体が多くて&1; つの既定のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="ae0ed-106">ただし、という&2; つ以上のバージョンがあるし、を既定のプロパティをオーバー ロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="ae0ed-107">詳細については、次を参照してください。[既定](../../../../visual-basic/language-reference/modifiers/default.md)します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="ae0ed-108">既定のプロパティを宣言するには</span><span class="sxs-lookup"><span data-stu-id="ae0ed-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="ae0ed-109">通常の方法でプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-109">Declare the property in the normal way.</span></span> <span data-ttu-id="ae0ed-110">指定しない、`Shared`または`Private`キーワードです。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="ae0ed-111">含める、`Default`プロパティの宣言でキーワードです。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="ae0ed-112">プロパティの&1; つ以上のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="ae0ed-113">少なくとも&1; つの引数を取らない既定のプロパティを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     <span data-ttu-id="ae0ed-114">[!code-vb[VbVbcnProcedures&17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-114">[!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span></span>  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="ae0ed-115">既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="ae0ed-115">To call a default property</span></span>  
  
1.  <span data-ttu-id="ae0ed-116">含むクラスまたは構造体の型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-116">Declare a variable of the containing class or structure type.</span></span>  
  
     <span data-ttu-id="ae0ed-117">[!code-vb[VbVbcnProcedures&#16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-117">[!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span></span>  
  
2.  <span data-ttu-id="ae0ed-118">プロパティ名を通常は式の中だけで、変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-118">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     <span data-ttu-id="ae0ed-119">[!code-vb[VbVbcnProcedures #&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-119">[!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span></span>  
  
3.  <span data-ttu-id="ae0ed-120">かっこで囲まれた引数リストを持つ変数名に従います。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-120">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="ae0ed-121">既定のプロパティは、少なくとも&1; つの引数を受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-121">A default property must take at least one argument.</span></span>  
  
     <span data-ttu-id="ae0ed-122">[!code-vb[VbVbcnProcedures&#20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-122">[!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span></span>  
  
4.  <span data-ttu-id="ae0ed-123">プロパティの既定値を取得するには、式の中で、または等しい、次の引数リストを含む、名前の変数を使用 (`=`)、代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-123">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="ae0ed-124">[!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-124">[!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span></span>  
  
5.  <span data-ttu-id="ae0ed-125">プロパティの既定値を設定するには、代入ステートメントの左側にある、引数リストを含むという名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-125">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="ae0ed-126">[!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-126">[!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span></span>  
  
6.  <span data-ttu-id="ae0ed-127">その他のプロパティにアクセスする場合と同様には、必ずという名前の変数と共に既定のプロパティ名を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-127">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     <span data-ttu-id="ae0ed-128">[!code-vb[VbVbcnProcedures&#19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-128">[!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae0ed-129">例</span><span class="sxs-lookup"><span data-stu-id="ae0ed-129">Example</span></span>  
 <span data-ttu-id="ae0ed-130">次の例では、クラスを既定のプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-130">The following example declares a default property on a class.</span></span>  
  
 <span data-ttu-id="ae0ed-131">[!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-131">[!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae0ed-132">例</span><span class="sxs-lookup"><span data-stu-id="ae0ed-132">Example</span></span>  
 <span data-ttu-id="ae0ed-133">次の例では、既定のプロパティを呼び出して`myProperty`クラスに`class1`します。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-133">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="ae0ed-134">次の&3; つの代入ステートメント内の値を格納する`myProperty`、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼び出しは、値を読み取ります</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-134">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 <span data-ttu-id="ae0ed-135">[!code-vb[VbVbcnProcedures&#13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="ae0ed-135">[!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span></span>  
  
 <span data-ttu-id="ae0ed-136">既定のプロパティの最も一般的な用途は、<xref:Microsoft.VisualBasic.Collection.Item%2A>さまざまなコレクション クラスのプロパティ</xref:Microsoft.VisualBasic.Collection.Item%2A>。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-136">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ae0ed-137">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="ae0ed-137">Robust Programming</span></span>  
 <span data-ttu-id="ae0ed-138">既定のプロパティは、ソース コードの文字のわずかな低下につながるはできるコード読み取るが困難です。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-138">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="ae0ed-139">クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合は使用できません特定その参照は、クラスまたは構造体そのものを既定のプロパティにアクセスするかどうか。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-139">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="ae0ed-140">コンパイラ エラーまたはランタイム ロジックの微妙なエラーにつながります。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-140">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="ae0ed-141">常を使用して、既定のプロパティのエラーの可能性を低くことができます多少、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックのコンパイラ タイプを設定する`On`です。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-141">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="ae0ed-142">使用を計画して、定義済みのクラスまたは構造体コードでは、決定する必要があります、既定のプロパティがあるかどうか、およびその場合、どのような名前です。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-142">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="ae0ed-143">このような短所は、ためには、既定のプロパティを定義しないことを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-143">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="ae0ed-144">コードを読みやすくは、常に明示的に参照するすべてのプロパティについても考慮も既定のプロパティ必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae0ed-144">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0ed-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae0ed-145">See Also</span></span>  
 <span data-ttu-id="ae0ed-146">[プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-146">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="ae0ed-147"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-147"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="ae0ed-148"> [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-148"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="ae0ed-149"> [既定値](../../../../visual-basic/language-reference/modifiers/default.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-149"> [Default](../../../../visual-basic/language-reference/modifiers/default.md) </span></span>  
<span data-ttu-id="ae0ed-150"> [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-150"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="ae0ed-151"> [方法: プロパティを作成します。](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-151"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="ae0ed-152"> [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-152"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="ae0ed-153"> [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-153"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="ae0ed-154"> [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="ae0ed-154"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="ae0ed-155"> [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="ae0ed-155"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
