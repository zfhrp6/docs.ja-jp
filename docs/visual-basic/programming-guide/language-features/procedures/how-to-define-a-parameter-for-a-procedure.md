---
title: "方法: プロシージャ (Visual Basic) のパラメーターを定義する |Microsoft ドキュメント"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 5a29bab1c18920d293c51d83d4d8cffdcefe936c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="d08ac-102">方法: プロシージャに対してパラメーターを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d08ac-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="d08ac-103">A*パラメーター*呼び出し元コードを呼び出すときに、プロシージャに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="d08ac-104">手順については、各パラメーター、変数を宣言すると、その名前とデータ型を指定するのと同じ方法を宣言します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="d08ac-105">また引き渡し方法を指定するパラメーターは省略可能かどうか。</span><span class="sxs-lookup"><span data-stu-id="d08ac-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="d08ac-106">詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="d08ac-107">プロシージャのパラメーターを定義するには</span><span class="sxs-lookup"><span data-stu-id="d08ac-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="d08ac-108">プロシージャの宣言では、プロシージャのパラメーター リストをコンマでの他のパラメーターから分離するパラメーター名を追加します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="d08ac-109">パラメーターのデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="d08ac-110">パラメーター名に続けて、`As`句データ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="d08ac-111">パラメーターの引き渡し方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="d08ac-112">通常を呼び出し元のコードにはその値を変更できるようにする手順をしない場合に、値でパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="d08ac-113">パラメーター名の前に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引き渡し方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="d08ac-114">詳細については、次を参照してください。[の相違点の間の値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="d08ac-115">渡しのパラメーターが省略可能な場合は、前に[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)は等号でパラメーターのデータ型に従います (`=`) および既定値です。</span><span class="sxs-lookup"><span data-stu-id="d08ac-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="d08ac-116">次の例のアウトラインを定義する、 `Sub`&3; つのパラメーターを持つプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="d08ac-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="d08ac-117">最初の&2; つは要求され、3 つ目は省略可能。</span><span class="sxs-lookup"><span data-stu-id="d08ac-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="d08ac-118">パラメーターの宣言は、パラメーター リストにコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     <span data-ttu-id="d08ac-119">[!code-vb[VbVbcnProcedures #&33;](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d08ac-119">[!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="d08ac-120">最初のパラメーターを受け入れる、`customer`オブジェクト、および`updateCustomer`に渡された変数を直接更新`c`引数が渡されるため[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-120">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="d08ac-121">渡されるために、プロシージャが最後の&2; つの引数の値を変更できません[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-121">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="d08ac-122">呼び出し元のコードがの値を指定しないかどうか、`level`パラメーター、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]既定値は 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-122">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="d08ac-123">型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off`、`As`パラメーターを定義するときに、句は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d08ac-123">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="d08ac-124">ただし、1 つのパラメーターを使用している場合、`As`句はすべての使用する必要です。</span><span class="sxs-lookup"><span data-stu-id="d08ac-124">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="d08ac-125">型チェック スイッチが場合`On`、`As`句はすべてのパラメーターの定義の必須です。</span><span class="sxs-lookup"><span data-stu-id="d08ac-125">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="d08ac-126">プログラミングのすべての要素のデータ型の指定と呼ばれます*厳密な型指定*します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-126">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="d08ac-127">設定すると`Option Strict On`、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]厳密な型指定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-127">When you set `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforces strong typing.</span></span> <span data-ttu-id="d08ac-128">これが強く推奨します、次の理由。</span><span class="sxs-lookup"><span data-stu-id="d08ac-128">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="d08ac-129">これにより、IntelliSense で変数とパラメーターをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-129">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="d08ac-130">これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d08ac-130">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="d08ac-131">これにより、コンパイラが型チェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-131">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="d08ac-132">これは、実行時のオーバーフローなどのエラーにより失敗するステートメントを検出するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d08ac-132">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="d08ac-133">サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d08ac-133">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="d08ac-134">コードの実行を高速になります。</span><span class="sxs-lookup"><span data-stu-id="d08ac-134">It results in faster execution of your code.</span></span> <span data-ttu-id="d08ac-135">これを&1; つの理由は、プログラミングの要素のデータ型が指定されていない場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが割り当てる、`Object`型です。</span><span class="sxs-lookup"><span data-stu-id="d08ac-135">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="d08ac-136">コンパイル済みのコードは、間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="d08ac-136">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08ac-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="d08ac-137">See Also</span></span>  
 <span data-ttu-id="d08ac-138">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-138">[Procedures](./index.md) </span></span>  
<span data-ttu-id="d08ac-139"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-139"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="d08ac-140"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-140"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="d08ac-141"> [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-141"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="d08ac-142"> [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-142"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="d08ac-143"> [再帰プロシージャ](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-143"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="d08ac-144"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-144"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="d08ac-145"> [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="d08ac-145"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="d08ac-146"> [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="d08ac-146"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
