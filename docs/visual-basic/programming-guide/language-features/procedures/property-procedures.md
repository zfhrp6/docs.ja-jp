---
title: "Property プロシージャ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbdf49d5c3eb5ef71b25a060d62f55f19098f445
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="1a168-102">Property プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a168-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="1a168-103">プロパティ プロシージャは、一連の[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]モジュール、クラスまたは構造体のカスタム プロパティを操作するステートメント。</span><span class="sxs-lookup"><span data-stu-id="1a168-103">A property procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="1a168-104">プロパティ プロシージャとも呼ばれます*プロパティ アクセサー*です。</span><span class="sxs-lookup"><span data-stu-id="1a168-104">Property procedures are also known as *property accessors*.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="1a168-105">次のプロパティ プロシージャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1a168-105"> provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="1a168-106">A`Get`プロシージャ、プロパティの値を返します。</span><span class="sxs-lookup"><span data-stu-id="1a168-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="1a168-107">式でプロパティにアクセスするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1a168-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="1a168-108">A`Set`プロシージャ、プロパティのオブジェクト参照を含め、値を設定します。</span><span class="sxs-lookup"><span data-stu-id="1a168-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="1a168-109">プロパティの値を代入するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1a168-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="1a168-110">使用して、対で通常プロパティ プロシージャを定義する、`Get`と`Set`がステートメントを定義できますいずれかの手順を単独でプロパティが読み取り専用の場合 ([Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)) または書き込み専用 ([設定ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="1a168-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="1a168-111">省略することができます、`Get`と`Set`自動実装プロパティを使用する場合、そのプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1a168-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="1a168-112">詳細については、「[自動実装プロパティ](./auto-implemented-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a168-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="1a168-113">プロパティは、クラス、構造体、およびモジュールで定義できます。</span><span class="sxs-lookup"><span data-stu-id="1a168-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="1a168-114">プロパティは、`Public`既定では、つまり、どこからでも呼び出すことができます、プロパティのコンテナーにアクセスできるアプリケーションでします。</span><span class="sxs-lookup"><span data-stu-id="1a168-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="1a168-115">プロパティと変数の比較を参照してください。[プロパティ間の相違点と Visual Basic における変数](./differences-between-properties-and-variables.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a168-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="1a168-116">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="1a168-116">Declaration Syntax</span></span>  
 <span data-ttu-id="1a168-117">プロパティ自体が囲まれたコードのブロックで定義されている、 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1a168-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="1a168-118">このブロック内で各プロパティ プロシージャは、宣言ステートメントで囲まれた内部ブロックとして表示されます。 (`Get`または`Set`) と一致する、`End`宣言します。</span><span class="sxs-lookup"><span data-stu-id="1a168-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="1a168-119">プロパティと、プロシージャの宣言の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a168-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="1a168-120">`Modifiers`を指定できますアクセス レベルおよびシャドウ、および、オーバーライド、共有、オーバー ロードに関する情報も、プロパティは、読み取り専用または書き込み専用かどうか。</span><span class="sxs-lookup"><span data-stu-id="1a168-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="1a168-121">`AccessLevel`上、`Get`または`Set`プロシージャは、プロパティ自体に指定されたアクセス レベルより限定的な任意のレベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1a168-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="1a168-122">詳細については、次を参照してください。 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a168-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="1a168-123">データの種類</span><span class="sxs-lookup"><span data-stu-id="1a168-123">Data Type</span></span>  
 <span data-ttu-id="1a168-124">プロパティのデータ型およびプリンシパルのアクセス レベルがで定義されている、`Property`ステートメントでは、プロパティ プロシージャではなく、します。</span><span class="sxs-lookup"><span data-stu-id="1a168-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="1a168-125">プロパティは、1 つだけのデータ型を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="1a168-125">A property can have only one data type.</span></span> <span data-ttu-id="1a168-126">たとえば、格納するプロパティを定義することはできません、`Decimal`値しますが、取得、`Double`値。</span><span class="sxs-lookup"><span data-stu-id="1a168-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="1a168-127">アクセス レベル</span><span class="sxs-lookup"><span data-stu-id="1a168-127">Access Level</span></span>  
 <span data-ttu-id="1a168-128">ただし、プロパティのプリンシパルのアクセス レベルを定義し、さらに、プロパティ プロシージャのいずれかでアクセス レベルを制限できます。</span><span class="sxs-lookup"><span data-stu-id="1a168-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="1a168-129">たとえば、定義することができます、`Public`プロパティし、定義、`Private Set`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="1a168-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="1a168-130">`Get`プロシージャまま`Public`です。</span><span class="sxs-lookup"><span data-stu-id="1a168-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="1a168-131">プロパティのプロシージャの 1 つに、アクセス レベルを変更することができすることができますのみがプリンシパルのアクセス レベルよりも制限します。</span><span class="sxs-lookup"><span data-stu-id="1a168-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="1a168-132">詳細については、次を参照してください。[する方法: 混合アクセス レベルを持つプロパティを宣言](./how-to-declare-a-property-with-mixed-access-levels.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a168-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="1a168-133">パラメーターの宣言</span><span class="sxs-lookup"><span data-stu-id="1a168-133">Parameter Declaration</span></span>  
 <span data-ttu-id="1a168-134">各パラメーターを宣言すると、同様の操作を行う[Sub プロシージャ](./sub-procedures.md)引き渡し方法がある点を除いて、`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="1a168-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="1a168-135">パラメーター リスト内の各パラメーターの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a168-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="1a168-136">パラメーターが省略可能な場合は、宣言の一部として既定値も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a168-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="1a168-137">既定値を指定する構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a168-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="1a168-138">プロパティ値</span><span class="sxs-lookup"><span data-stu-id="1a168-138">Property Value</span></span>  
 <span data-ttu-id="1a168-139">`Get`プロシージャ、戻り値がプロパティの値として呼び出し元の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="1a168-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="1a168-140">`Set`プロシージャ、新しいプロパティ値は、のパラメーターに渡される、`Set`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1a168-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="1a168-141">パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a168-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="1a168-142">コンパイラが暗黙的なパラメーターを使用して、パラメーターを宣言していない場合`Value`をプロパティに割り当てられる新しい値を表します。</span><span class="sxs-lookup"><span data-stu-id="1a168-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="1a168-143">呼び出し構文</span><span class="sxs-lookup"><span data-stu-id="1a168-143">Calling Syntax</span></span>  
 <span data-ttu-id="1a168-144">プロパティ プロシージャをプロパティに参照することによって暗黙的を呼び出すとします。</span><span class="sxs-lookup"><span data-stu-id="1a168-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="1a168-145">使用するプロパティの名前、変数の名前を使用すると同じ方法は、省略できないすべての引数の値を指定する必要がある点を除いて、引数リストをかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a168-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="1a168-146">引数がない場合は、かっこを省略することができます。</span><span class="sxs-lookup"><span data-stu-id="1a168-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="1a168-147">暗黙的な呼び出しの構文、`Set`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a168-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="1a168-148">暗黙的な呼び出しの構文、`Get`手順のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1a168-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="1a168-149">宣言と呼び出しの図</span><span class="sxs-lookup"><span data-stu-id="1a168-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="1a168-150">次のプロパティは、2 つの構成名、名、姓と名として完全な名前を格納します。</span><span class="sxs-lookup"><span data-stu-id="1a168-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="1a168-151">呼び出し元のコードを読み取るとき`fullName`、`Get`プロシージャは次の 2 つの構成名を結合し、完全な名前を返します。</span><span class="sxs-lookup"><span data-stu-id="1a168-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="1a168-152">呼び出し元のコードは、新しい完全な名前を割り当てを行うとき、`Set`プロシージャを次の 2 つの部分に分割しようとしました。</span><span class="sxs-lookup"><span data-stu-id="1a168-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="1a168-153">場所が見つからない場合、名前としてすべて格納します。</span><span class="sxs-lookup"><span data-stu-id="1a168-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="1a168-154">次の例では、通常、プロパティ プロシージャ呼び出しの`fullName`します。</span><span class="sxs-lookup"><span data-stu-id="1a168-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1a168-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a168-155">See Also</span></span>  
 [<span data-ttu-id="1a168-156">手順</span><span class="sxs-lookup"><span data-stu-id="1a168-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1a168-157">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1a168-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="1a168-158">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1a168-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="1a168-159">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="1a168-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="1a168-160">Visual Basic でのプロパティと変数の違い</span><span class="sxs-lookup"><span data-stu-id="1a168-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="1a168-161">方法 : プロパティを作成する</span><span class="sxs-lookup"><span data-stu-id="1a168-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="1a168-162">方法 : プロパティ プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1a168-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="1a168-163">方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す</span><span class="sxs-lookup"><span data-stu-id="1a168-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="1a168-164">方法 : プロパティに値を格納する</span><span class="sxs-lookup"><span data-stu-id="1a168-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="1a168-165">方法 : プロパティから値を取得する</span><span class="sxs-lookup"><span data-stu-id="1a168-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
