---
title: "Property プロシージャ (Visual Basic) |Microsoft ドキュメント"
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
- Set statement, Property procedures
- Visual Basic code, procedures
- return values, Property procedures
- syntax, Property procedures
- procedures, property
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], custom
- property procedures
- Get statement, property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6ba662a8cf9748b719bfbd7205ce65989e79d05a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="11df3-102">Property プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11df3-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="11df3-103">Property プロシージャは、一連の[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュール、クラスまたは構造体のカスタム プロパティを操作するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="11df3-103">A property procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="11df3-104">プロパティ プロシージャとも呼ばれます*プロパティ アクセサー*します。</span><span class="sxs-lookup"><span data-stu-id="11df3-104">Property procedures are also known as *property accessors*.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="11df3-105">プロパティの次の手順を示します。</span><span class="sxs-lookup"><span data-stu-id="11df3-105"> provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="11df3-106">A`Get`プロパティの値を返します。</span><span class="sxs-lookup"><span data-stu-id="11df3-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="11df3-107">式の中でプロパティにアクセスするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="11df3-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="11df3-108">A`Set`プロシージャ、プロパティのオブジェクト参照を含め、値を設定します。</span><span class="sxs-lookup"><span data-stu-id="11df3-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="11df3-109">プロパティの値を代入するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="11df3-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="11df3-110">使用して、ペアで通常プロパティ プロシージャを定義する、`Get`と`Set`プロパティが読み取り専用である場合は、ステートメントがからまたは編集手順だけでに定義することができます ([Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)) または書き込み専用 ([Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="11df3-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="11df3-111">省略することができます、`Get`と`Set`プロシージャは、自動実装プロパティを使用する場合。</span><span class="sxs-lookup"><span data-stu-id="11df3-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="11df3-112">詳細については、次を参照してください。 [Auto-Implemented プロパティ](./auto-implemented-properties.md)します。</span><span class="sxs-lookup"><span data-stu-id="11df3-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="11df3-113">プロパティは、クラス、構造体、およびモジュールで定義できます。</span><span class="sxs-lookup"><span data-stu-id="11df3-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="11df3-114">プロパティは、`Public`既定では、つまりどこからでも呼び出すことが、プロパティのコンテナーにアクセスできるアプリケーションにします。</span><span class="sxs-lookup"><span data-stu-id="11df3-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="11df3-115">プロパティと変数の比較では、次を参照してください。[プロパティ間の相違点と Visual Basic における変数](./differences-between-properties-and-variables.md)します。</span><span class="sxs-lookup"><span data-stu-id="11df3-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="11df3-116">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="11df3-116">Declaration Syntax</span></span>  
 <span data-ttu-id="11df3-117">プロパティ自体が囲まれたコードのブロックで定義されている、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="11df3-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="11df3-118">宣言ステートメントで囲んだ内部ブロックとしてこのブロック内では各プロパティ プロシージャが表示されます (`Get`または`Set`) と、一致する`End`宣言します。</span><span class="sxs-lookup"><span data-stu-id="11df3-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="11df3-119">プロパティとそのプロシージャの宣言の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="11df3-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="11df3-120">`Modifiers`を指定できますアクセス レベルと、オーバー ロード、オーバーライド、共有、およびシャドウに関する情報も、プロパティは、読み取り専用または書き込み専用かどうか。</span><span class="sxs-lookup"><span data-stu-id="11df3-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="11df3-121">`AccessLevel`上、`Get`または`Set`プロシージャは、プロパティ自体に対して指定されたアクセス レベルより限定的な任意のレベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="11df3-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="11df3-122">詳細については、次を参照してください。 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="11df3-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="11df3-123">データの種類</span><span class="sxs-lookup"><span data-stu-id="11df3-123">Data Type</span></span>  
 <span data-ttu-id="11df3-124">プロパティのデータ型とプリンシパルのアクセス レベルが定義されて、`Property`プロパティ プロシージャではなく、ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="11df3-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="11df3-125">プロパティは、1 つだけのデータ型であることができます。</span><span class="sxs-lookup"><span data-stu-id="11df3-125">A property can have only one data type.</span></span> <span data-ttu-id="11df3-126">などを格納するプロパティを定義することはできません、`Decimal`値が、取得、`Double`値。</span><span class="sxs-lookup"><span data-stu-id="11df3-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="11df3-127">アクセス レベル</span><span class="sxs-lookup"><span data-stu-id="11df3-127">Access Level</span></span>  
 <span data-ttu-id="11df3-128">ただし、プロパティのプリンシパルのアクセス レベルを定義し、さらに、プロパティ プロシージャのいずれかでアクセス レベルを制限できます。</span><span class="sxs-lookup"><span data-stu-id="11df3-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="11df3-129">たとえば、定義、`Public`プロパティし、定義、`Private Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="11df3-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="11df3-130">`Get`プロシージャまま`Public`します。</span><span class="sxs-lookup"><span data-stu-id="11df3-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="11df3-131">プロパティのプロシージャの&1; つに、アクセス レベルを変更することができます行いすることができますのみプリンシパルのアクセス レベル以上に制限します。</span><span class="sxs-lookup"><span data-stu-id="11df3-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="11df3-132">詳細については、次を参照してください。[方法: 混合アクセス レベルを持つプロパティを宣言](./how-to-declare-a-property-with-mixed-access-levels.md)します。</span><span class="sxs-lookup"><span data-stu-id="11df3-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="11df3-133">パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="11df3-133">Parameter Declaration</span></span>  
 <span data-ttu-id="11df3-134">各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)渡すメカニズムである必要がありますが、`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="11df3-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="11df3-135">パラメーター リスト内の各パラメーターの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="11df3-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="11df3-136">パラメーターが省略可能な場合も、その宣言の一部として既定値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11df3-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="11df3-137">既定値を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="11df3-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="11df3-138">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="11df3-138">Property Value</span></span>  
 <span data-ttu-id="11df3-139">`Get`プロシージャの戻り値は、プロパティの値として呼び出し元の式に提供します。</span><span class="sxs-lookup"><span data-stu-id="11df3-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="11df3-140">`Set`プロシージャでは、新しいプロパティ値のパラメーターに渡される、`Set`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="11df3-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="11df3-141">パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11df3-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="11df3-142">コンパイラが暗黙の型のパラメーターを使用してパラメーターを宣言していない場合`Value`をプロパティに割り当てられる新しい値を表します。</span><span class="sxs-lookup"><span data-stu-id="11df3-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="11df3-143">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="11df3-143">Calling Syntax</span></span>  
 <span data-ttu-id="11df3-144">プロパティ プロシージャは、プロパティを参照することによって暗黙的を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="11df3-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="11df3-145">使用するプロパティの名前、変数の名前を使用すると同じ方法が、省略可能ではないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="11df3-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="11df3-146">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="11df3-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="11df3-147">暗黙の呼び出しの構文、`Set`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="11df3-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="11df3-148">暗黙の呼び出しの構文、`Get`手順は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="11df3-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="11df3-149">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="11df3-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="11df3-150">次のプロパティは、2 つの構成名、名、姓と名として完全な名前を格納します。</span><span class="sxs-lookup"><span data-stu-id="11df3-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="11df3-151">呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは、2 つの構成名を結合し、完全な名前を返します。</span><span class="sxs-lookup"><span data-stu-id="11df3-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="11df3-152">呼び出し元のコードが新しいの完全名を割り当てるときに、`Set`プロシージャを次の&2; つの部分に分割を試行します。</span><span class="sxs-lookup"><span data-stu-id="11df3-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="11df3-153">場所が見つからない場合は、すべてを最初の名前として格納します。</span><span class="sxs-lookup"><span data-stu-id="11df3-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 <span data-ttu-id="11df3-154">[!code-vb[VbVbcnProcedures&#8;](./codesnippet/VisualBasic/property-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="11df3-154">[!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="11df3-155">次の例では、一般的なプロシージャを呼び出して、プロパティの`fullName`です。</span><span class="sxs-lookup"><span data-stu-id="11df3-155">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 <span data-ttu-id="11df3-156">[!code-vb[VbVbcnProcedures&#9;](./codesnippet/VisualBasic/property-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="11df3-156">[!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11df3-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="11df3-157">See Also</span></span>  
 <span data-ttu-id="11df3-158">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-158">[Procedures](./index.md) </span></span>  
<span data-ttu-id="11df3-159"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-159"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="11df3-160"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-160"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="11df3-161"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-161"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="11df3-162"> [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-162"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="11df3-163"> [方法: プロパティを作成します。](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-163"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="11df3-164"> [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-164"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="11df3-165"> [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-165"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="11df3-166"> [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="11df3-166"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="11df3-167"> [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="11df3-167"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
