---
title: "Visual Basic におけるプロシージャ"
ms.custom: 
ms.date: 2017-04-28
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, structured code
- Visual Basic code, procedures
- procedures, types of
- structured code, procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fd1a369ecfc1fa23cba694941fa47ab872ca1368
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="procedures-in-visual-basic"></a><span data-ttu-id="753bc-102">Visual Basic におけるプロシージャ</span><span class="sxs-lookup"><span data-stu-id="753bc-102">Procedures in Visual Basic</span></span>
<span data-ttu-id="753bc-103">*プロシージャ*は、宣言ステートメント (`Function`、`Sub`、`Operator`、`Get`、`Set`) とこれに一致する `End` 宣言で囲まれた、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="753bc-103">A *procedure* is a block of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by a declaration statement (`Function`, `Sub`, `Operator`, `Get`, `Set`) and a matching `End` declaration.</span></span> <span data-ttu-id="753bc-104">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のすべての実行可能なステートメントは何らかのプロシージャに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="753bc-104">All executable statements in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must be within some procedure.</span></span>  
  
## <a name="calling-a-procedure"></a><span data-ttu-id="753bc-105">プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="753bc-105">Calling a Procedure</span></span>  
 <span data-ttu-id="753bc-106">コード内の他の場所からプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="753bc-106">You invoke a procedure from some other place in the code.</span></span> <span data-ttu-id="753bc-107">これは、*プロシージャ コール*と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="753bc-107">This is known as a *procedure call*.</span></span> <span data-ttu-id="753bc-108">プロシージャの実行が終了すると、それを呼び出したコード (*呼び出しコード*と呼ばれます) に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="753bc-108">When the procedure is finished running, it returns control to the code that invoked it, which is known as the *calling code*.</span></span> <span data-ttu-id="753bc-109">呼び出しコードは、名前でプロシージャを指定して、これに制御を転送するステートメント、またはステートメント内の式です。</span><span class="sxs-lookup"><span data-stu-id="753bc-109">The calling code is a statement, or an expression within a statement, that specifies the procedure by name and transfers control to it.</span></span>  
  
## <a name="returning-from-a-procedure"></a><span data-ttu-id="753bc-110">プロシージャからの復帰</span><span class="sxs-lookup"><span data-stu-id="753bc-110">Returning from a Procedure</span></span>  
 <span data-ttu-id="753bc-111">プロシージャは、実行が終了すると、呼び出しコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="753bc-111">A procedure returns control to the calling code when it has finished running.</span></span> <span data-ttu-id="753bc-112">これを行うには、[Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)、プロシージャに適した [Exit ステートメント](../../../../visual-basic/language-reference/statements/exit-statement.md)、またはプロシージャの [End \<キーワード> ステートメント](../../../../visual-basic/language-reference/statements/end-keyword-statement.md)を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-112">To do this, it can use a [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), the appropriate [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) statement for the procedure, or the procedure's [End \<keyword> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) statement.</span></span> <span data-ttu-id="753bc-113">これで、プロシージャ コールの次の時点で、制御が呼び出しコードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="753bc-113">Control then passes to the calling code following the point of the procedure call.</span></span>  
  
-   <span data-ttu-id="753bc-114">`Return` ステートメントでは、ただちに呼び出しコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="753bc-114">With a `Return` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="753bc-115">`Return` ステートメントより後のステートメントは実行されません。</span><span class="sxs-lookup"><span data-stu-id="753bc-115">Statements following the `Return` statement do not run.</span></span> <span data-ttu-id="753bc-116">同じプロシージャ内に複数の `Return` ステートメントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-116">You can have more than one `Return` statement in the same procedure.</span></span>  
  
-   <span data-ttu-id="753bc-117">`Exit Sub` または `Exit Function` ステートメントでは、ただちに呼び出しコードに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="753bc-117">With an `Exit Sub` or `Exit Function` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="753bc-118">`Exit` ステートメントより後のステートメントは実行されません。</span><span class="sxs-lookup"><span data-stu-id="753bc-118">Statements following the `Exit` statement do not run.</span></span> <span data-ttu-id="753bc-119">同じプロシージャ内に複数の `Exit` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit` ステートメントを混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-119">You can have more than one `Exit` statement in the same procedure, and you can mix `Return` and `Exit` statements in the same procedure.</span></span>  
  
-   <span data-ttu-id="753bc-120">プロシージャに `Return` または `Exit` のステートメントが含まれていない場合、プロシージャ本体の最後のステートメントの後の `End Sub` または `End Function`、`End Get` または `End Set` で終了します。</span><span class="sxs-lookup"><span data-stu-id="753bc-120">If a procedure has no `Return` or `Exit` statements, it concludes with an `End Sub` or `End Function`, `End Get`, or `End Set` statement following the last statement of the procedure body.</span></span> <span data-ttu-id="753bc-121">`End` ステートメントはただちに呼び出しコードに制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="753bc-121">The `End` statement returns control immediately to the calling code.</span></span> <span data-ttu-id="753bc-122">`End` ステートメントは、プロシージャ内に 1 つだけ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-122">You can have only one `End` statement in a procedure.</span></span>  
  
## <a name="parameters-and-arguments"></a><span data-ttu-id="753bc-123">パラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="753bc-123">Parameters and Arguments</span></span>  
 <span data-ttu-id="753bc-124">プロシージャは、ほとんどの場合、呼び出すたびにデータごとに動作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="753bc-124">In most cases, a procedure needs to operate on different data each time you call it.</span></span> <span data-ttu-id="753bc-125">この情報は、プロシージャ コールの一部としてプロシージャに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-125">You can pass this information to the procedure as part of the procedure call.</span></span> <span data-ttu-id="753bc-126">プロシージャは、*パラメーター*を 0 個、またはそれ以上でも定義することができ、それぞれが渡す必要がある値を表しています。</span><span class="sxs-lookup"><span data-stu-id="753bc-126">The procedure defines zero or more *parameters*, each of which represents a value it expects you to pass to it.</span></span> <span data-ttu-id="753bc-127">プロシージャ定義の各パラメーターに相当するのが、プロシージャ コールの*引数*です。</span><span class="sxs-lookup"><span data-stu-id="753bc-127">Corresponding to each parameter in the procedure definition is an *argument* in the procedure call.</span></span> <span data-ttu-id="753bc-128">引数は、指定したプロシージャ コールの対応するパラメーターに渡される値を表しています。</span><span class="sxs-lookup"><span data-stu-id="753bc-128">An argument represents the value you pass to the corresponding parameter in a given procedure call.</span></span>  
  
## <a name="types-of-procedures"></a><span data-ttu-id="753bc-129">プロシージャの種類</span><span class="sxs-lookup"><span data-stu-id="753bc-129">Types of Procedures</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="753bc-130"> では、次のような種類のプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="753bc-130"> uses several types of procedures:</span></span>  
  
-   <span data-ttu-id="753bc-131">[Sub プロシージャ](./sub-procedures.md)はアクションを実行しますが、呼び出しコードに値を返しません。</span><span class="sxs-lookup"><span data-stu-id="753bc-131">[Sub Procedures](./sub-procedures.md) perform actions but do not return a value to the calling code.</span></span>  
  
-   <span data-ttu-id="753bc-132">イベント処理プロシージャは、ユーザーの操作またはプログラムの起動によって発生したイベントに応答して実行される `Sub` プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="753bc-132">Event-handling procedures are `Sub` procedures that execute in response to an event raised by user action or by an occurrence in a program.</span></span>  
  
-   <span data-ttu-id="753bc-133">[Function プロシージャ](./function-procedures.md)は、呼び出しコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="753bc-133">[Function Procedures](./function-procedures.md) return a value to the calling code.</span></span> <span data-ttu-id="753bc-134">返す前に他の操作を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-134">They can perform other actions before returning.</span></span>

    <span data-ttu-id="753bc-135">C# で書かれた一部の関数は、*参照戻り値*を返します。</span><span class="sxs-lookup"><span data-stu-id="753bc-135">Some functions written in C# return a *reference return value*.</span></span> <span data-ttu-id="753bc-136">関数の呼び出し元は、戻り値を変更することができ、この変更は呼び出されたオブジェクトの状態に反映されます。</span><span class="sxs-lookup"><span data-stu-id="753bc-136">Function callers can modify the return value, and this modification is reflected in the state of the called object.</span></span> <span data-ttu-id="753bc-137">Visual Basic は参照によって値を返すことはできませんが、Visual Basic 2017 から、Visual Basic のコードで参照戻り値を使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="753bc-137">Starting with Visual Basic 2017, Visual Basic code can consume reference return values, although it cannot return a value by reference.</span></span> <span data-ttu-id="753bc-138">詳細については、[参照戻り値](ref-return-values.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="753bc-138">For more information, see [Reference return values](ref-return-values.md).</span></span>
  
-   <span data-ttu-id="753bc-139">[プロパティ プロシージャ](./property-procedures.md)は、オブジェクトまたはモジュールのプロパティの値を返し、割り当てます。</span><span class="sxs-lookup"><span data-stu-id="753bc-139">[Property Procedures](./property-procedures.md) return and assign values of properties on objects or modules.</span></span>  
  
-   <span data-ttu-id="753bc-140">[演算子プロシージャ](./operator-procedures.md)は、オペランドの一方または両方が新しく定義されたクラスまたは構造体である場合に、標準の演算子の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="753bc-140">[Operator Procedures](./operator-procedures.md) define the behavior of a standard operator when one or both of the operands is a newly-defined class or structure.</span></span>  
  
-   <span data-ttu-id="753bc-141">[Visual Basic におけるジェネリック プロシージャ](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)は、標準のパラメーターだけでなく 1 つまたは複数の*型パラメーター*も定義するため、呼び出しコードが呼び出しのたびに特定のデータ型を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-141">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) define one or more *type parameters* in addition to their normal parameters, so the calling code can pass specific data types each time it makes a call.</span></span>  
  
## <a name="procedures-and-structured-code"></a><span data-ttu-id="753bc-142">プロシージャと構造化されたコード</span><span class="sxs-lookup"><span data-stu-id="753bc-142">Procedures and Structured Code</span></span>  
 <span data-ttu-id="753bc-143">アプリケーションの実行可能コードのすべての行が、`Main`、 `calculate`、`Button1_Click` などの何らかのプロシージャの内部にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="753bc-143">Every line of executable code in your application must be inside some procedure, such as `Main`, `calculate`, or `Button1_Click`.</span></span> <span data-ttu-id="753bc-144">大きなプロシージャを小さなプロシージャに分割すると、アプリケーションが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="753bc-144">If you subdivide large procedures into smaller ones, your application is more readable.</span></span>  
  
 <span data-ttu-id="753bc-145">プロシージャは、頻繁に使用する計算、テキストやコントロールの操作、データベースの操作など、繰り返される、または共有されるタスクを実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="753bc-145">Procedures are useful for performing repeated or shared tasks, such as frequently used calculations, text and control manipulation, and database operations.</span></span> <span data-ttu-id="753bc-146">プロシージャはコード内のさまざまな場所から呼び出すことができるため、プロシージャをアプリケーションの文書パーツとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-146">You can call a procedure from many different places in your code, so you can use procedures as building blocks for your application.</span></span>  
  
 <span data-ttu-id="753bc-147">プロシージャでコードを構成すると、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="753bc-147">Structuring your code with procedures gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="753bc-148">プロシージャを使用して、プログラムを個々の論理単位に分割できます。</span><span class="sxs-lookup"><span data-stu-id="753bc-148">Procedures allow you to break your programs into discrete logical units.</span></span> <span data-ttu-id="753bc-149">プロシージャを使用せずにプログラム全体をデバッグするよりも、個別の単位の方が簡単にデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="753bc-149">You can debug separate units more easily than you can debug an entire program without procedures.</span></span>  
  
-   <span data-ttu-id="753bc-150">1 つのプログラムで使用するために開発したプロシージャを、他のプログラムでも使用できます。多くの場合、プログラムをほとんどまたはまったく変更せずに使用できます。</span><span class="sxs-lookup"><span data-stu-id="753bc-150">After you develop procedures for use in one program, you can use them in other programs, often with little or no modification.</span></span> <span data-ttu-id="753bc-151">これにより、コードの重複を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="753bc-151">This helps you avoid code duplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753bc-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="753bc-152">See Also</span></span>  
 <span data-ttu-id="753bc-153">[方法: プロシージャを作成する](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-153">[How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
 <span data-ttu-id="753bc-154">[Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-154">[Sub Procedures](./sub-procedures.md) </span></span>  
 <span data-ttu-id="753bc-155">[Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-155">[Function Procedures](./function-procedures.md) </span></span>  
 <span data-ttu-id="753bc-156">[プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-156">[Property Procedures](./property-procedures.md) </span></span>  
 <span data-ttu-id="753bc-157">[演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-157">[Operator Procedures](./operator-procedures.md) </span></span>  
 <span data-ttu-id="753bc-158">[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-158">[Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
 <span data-ttu-id="753bc-159">[再帰プロシージャ](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-159">[Recursive Procedures](./recursive-procedures.md) </span></span>  
 <span data-ttu-id="753bc-160">[プロシージャのオーバーロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-160">[Procedure Overloading](./procedure-overloading.md) </span></span>  
 <span data-ttu-id="753bc-161">[Visual Basic におけるジェネリック プロシージャ](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="753bc-161">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span></span>  
 [<span data-ttu-id="753bc-162">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="753bc-162">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

