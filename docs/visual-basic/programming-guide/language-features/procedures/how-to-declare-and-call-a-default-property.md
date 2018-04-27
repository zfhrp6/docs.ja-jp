---
title: '方法: 既定のプロパティを宣言して呼び出す (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c4f471eba42e47d6bef45a4d38abc0cbd2d32bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="3a70c-102">方法: 既定のプロパティを宣言して呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a70c-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="3a70c-103">A*既定プロパティ*クラスまたは構造体のプロパティで指定することがなく、コードにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3a70c-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="3a70c-104">呼び出し元のコードは、クラスまたは構造体がない、プロパティ、およびコンテキスト プロパティへのアクセスを許可、Visual Basic が存在する場合に、そのクラスまたは構造体の既定のプロパティにアクセスを解決します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="3a70c-105">クラスまたは構造体は最大で 1 つの既定プロパティをできます。</span><span class="sxs-lookup"><span data-stu-id="3a70c-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="3a70c-106">ただし、既定のプロパティをオーバー ロードして、という 2 つ以上のバージョンであります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="3a70c-107">詳細については、次を参照してください。[既定](../../../../visual-basic/language-reference/modifiers/default.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a70c-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="3a70c-108">既定のプロパティを宣言するには</span><span class="sxs-lookup"><span data-stu-id="3a70c-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="3a70c-109">通常の方法でプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-109">Declare the property in the normal way.</span></span> <span data-ttu-id="3a70c-110">指定しない、`Shared`または`Private`キーワード。</span><span class="sxs-lookup"><span data-stu-id="3a70c-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="3a70c-111">含める、`Default`プロパティ宣言でキーワード。</span><span class="sxs-lookup"><span data-stu-id="3a70c-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="3a70c-112">プロパティの 1 つ以上のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="3a70c-113">少なくとも 1 つの引数を取らない既定のプロパティを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="3a70c-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="3a70c-114">既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3a70c-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="3a70c-115">それを含むクラスまたは構造体の型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="3a70c-116">プロパティ名を通常含めるは式の中だけで、変数名を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="3a70c-117">かっこ内に引数リストを持つ変数の名前に従います。</span><span class="sxs-lookup"><span data-stu-id="3a70c-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="3a70c-118">既定のプロパティは、少なくとも 1 つの引数を受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="3a70c-119">プロパティの既定値を取得するには、引数リスト、または等しい、次の式で指定した変数の名前を使用 (`=`) 代入ステートメントにサインインします。</span><span class="sxs-lookup"><span data-stu-id="3a70c-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="3a70c-120">既定のプロパティ値を設定するには、代入ステートメントの左側にある、引数リストを持つという名前の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="3a70c-121">他のプロパティにアクセスする場合と同様、という名前の変数と共に既定のプロパティ名を必ず指定することができます。</span><span class="sxs-lookup"><span data-stu-id="3a70c-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a70c-122">例</span><span class="sxs-lookup"><span data-stu-id="3a70c-122">Example</span></span>  
 <span data-ttu-id="3a70c-123">次の例では、クラスを既定のプロパティを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a70c-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a70c-124">例</span><span class="sxs-lookup"><span data-stu-id="3a70c-124">Example</span></span>  
 <span data-ttu-id="3a70c-125">次の例では、既定のプロパティを呼び出して`myProperty`クラス`class1`です。</span><span class="sxs-lookup"><span data-stu-id="3a70c-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="3a70c-126">次の 3 つの代入ステートメントで値を格納する`myProperty`、および<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>呼び出しは、値を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="3a70c-127">既定のプロパティの最も一般的な用途は、<xref:Microsoft.VisualBasic.Collection.Item%2A>さまざまなコレクション クラスのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3a70c-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3a70c-128">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="3a70c-128">Robust Programming</span></span>  
 <span data-ttu-id="3a70c-129">既定のプロパティは、ソース コードの文字のわずかな低下につながるが行えるコード読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="3a70c-130">クラスまたは構造体名への参照を行うときに、呼び出し元のコードがクラスまたは構造に習熟していない場合は指定できません特定その参照が、クラスまたは構造体自体、または既定のプロパティにアクセスするかどうか。</span><span class="sxs-lookup"><span data-stu-id="3a70c-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="3a70c-131">これは、コンパイラ エラーまたは実行時の微妙な論理エラーを可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="3a70c-132">常を使用して既定のプロパティのエラーの可能性を低くことができます多少、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)をチェックインするコンパイラ タイプを設定する`On`です。</span><span class="sxs-lookup"><span data-stu-id="3a70c-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="3a70c-133">使用を計画して、定義済みのクラスまたは構造体、コード内を決定する必要がありますを既定のプロパティがあるかどうかと、その場合、どのような名前です。</span><span class="sxs-lookup"><span data-stu-id="3a70c-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="3a70c-134">これらの欠点のためには、既定のプロパティを定義しないを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3a70c-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="3a70c-135">コードの読みやすさも常にすべてのプロパティを明示的に参照を検討も既定のプロパティする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a70c-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a70c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a70c-136">See Also</span></span>  
 [<span data-ttu-id="3a70c-137">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="3a70c-137">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="3a70c-138">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="3a70c-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="3a70c-139">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="3a70c-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="3a70c-140">既定値</span><span class="sxs-lookup"><span data-stu-id="3a70c-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)  
 [<span data-ttu-id="3a70c-141">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="3a70c-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="3a70c-142">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="3a70c-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="3a70c-143">方法 : 複数のアクセス レベルを持つプロパティを宣言する</span><span class="sxs-lookup"><span data-stu-id="3a70c-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="3a70c-144">方法 : プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="3a70c-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="3a70c-145">方法 : プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="3a70c-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="3a70c-146">方法 : プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="3a70c-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
