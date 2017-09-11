---
title: "プロパティまたは文字列の名前 (Visual Basic) を使用して、メソッドの呼び出し |Microsoft ドキュメント"
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
- passing operators
- strings [Visual Basic], passing new operators as
- objects [Visual Basic], setting properties
- setting properties, object properties at run time
- method calls, strings
- methods [Visual Basic], calling with string names
- calling methods, string names
- properties [Visual Basic], setting at run time
- CallByName function
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
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
ms.openlocfilehash: 6de5e655b3d4d42283b81507d7f08e0eb0b9424d
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="calling-a-property-or-method-using-a-string-name-visual-basic"></a><span data-ttu-id="c57ee-102">文字列名によるプロパティまたはメソッドの呼び出し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c57ee-102">Calling a Property or Method Using a String Name (Visual Basic)</span></span>
<span data-ttu-id="c57ee-103">ほとんどの場合は、デザイン時にプロパティとオブジェクトのメソッドを検出し、それらを処理するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="c57ee-103">In most cases, you can discover the properties and methods of an object at design time, and write code to handle them.</span></span> <span data-ttu-id="c57ee-104">ただし、場合によっては、ご存じないオブジェクトのプロパティとメソッドを事前にまたはプロパティを指定するか、実行時にメソッドを実行するエンドユーザーを有効化の柔軟性、たい場合があります。</span><span class="sxs-lookup"><span data-stu-id="c57ee-104">However, in some cases you may not know about an object's properties and methods in advance, or you may just want the flexibility of enabling an end user to specify properties or execute methods at run time.</span></span>  
  
## <a name="callbyname-function"></a><span data-ttu-id="c57ee-105">CallByName 関数</span><span class="sxs-lookup"><span data-stu-id="c57ee-105">CallByName Function</span></span>  
 <span data-ttu-id="c57ee-106">たとえば、オペレーターを COM コンポーネントに渡すことによって、ユーザーが入力した式を評価するクライアント アプリケーションについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="c57ee-106">Consider, for example, a client application that evaluates expressions entered by the user by passing an operator to a COM component.</span></span> <span data-ttu-id="c57ee-107">新しい演算子を必要とするコンポーネントを常に新しい関数を追加するとします。</span><span class="sxs-lookup"><span data-stu-id="c57ee-107">Suppose you are constantly adding new functions to the component that require new operators.</span></span> <span data-ttu-id="c57ee-108">標準のオブジェクトのアクセス方法を使用する場合は、再コンパイルし、新しい演算子を使用できるように、クライアント アプリケーションを再配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c57ee-108">When you use standard object access techniques, you must recompile and redistribute the client application before it could use the new operators.</span></span> <span data-ttu-id="c57ee-109">これを回避するには、使用することができます、`CallByName`アプリケーションを変更することがなく、文字列として新しい演算子を渡す関数です。</span><span class="sxs-lookup"><span data-stu-id="c57ee-109">To avoid this, you can use the `CallByName` function to pass the new operators as strings, without changing the application.</span></span>  
  
 <span data-ttu-id="c57ee-110">`CallByName`関数では、実行時にプロパティまたはメソッドを指定する文字列を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c57ee-110">The `CallByName` function lets you use a string to specify a property or method at run time.</span></span> <span data-ttu-id="c57ee-111">署名、`CallByName`関数は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c57ee-111">The signature for the `CallByName` function looks like this:</span></span>  
  
 <span data-ttu-id="c57ee-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span><span class="sxs-lookup"><span data-stu-id="c57ee-112">*Result* = `CallByName`(*Object*, *ProcedureName*, *CallType*, *Arguments*())</span></span>  
  
 <span data-ttu-id="c57ee-113">最初の引数*オブジェクト*、対象とするオブジェクトの名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c57ee-113">The first argument, *Object*, takes the name of the object you want to act upon.</span></span> <span data-ttu-id="c57ee-114">*ProcedureName*引数には、呼び出されるメソッドまたはプロパティ プロシージャの名前を表す文字列。</span><span class="sxs-lookup"><span data-stu-id="c57ee-114">The *ProcedureName* argument takes a string that contains the name of the method or property procedure to be invoked.</span></span> <span data-ttu-id="c57ee-115">*CallType*引数を呼び出すプロシージャの種類を表す定数。 メソッド (`Microsoft.VisualBasic.CallType.Method`)、読み込まれるプロパティ (`Microsoft.VisualBasic.CallType.Get`)、またはプロパティの設定 (`Microsoft.VisualBasic.CallType.Set`)。</span><span class="sxs-lookup"><span data-stu-id="c57ee-115">The *CallType* argument takes a constant that represents the type of procedure to invoke: a method (`Microsoft.VisualBasic.CallType.Method`), a property read (`Microsoft.VisualBasic.CallType.Get`), or a property set (`Microsoft.VisualBasic.CallType.Set`).</span></span> <span data-ttu-id="c57ee-116">*引数*の引数は省略可能な型の配列を受け取る`Object`プロシージャに引数を格納しています。</span><span class="sxs-lookup"><span data-stu-id="c57ee-116">The *Arguments* argument, which is optional, takes an array of type `Object` that contains any arguments to the procedure.</span></span>  
  
 <span data-ttu-id="c57ee-117">使用する`CallByName`からオブジェクトまたはクラスが、現在のソリューションには、最もよく使用される COM オブジェクトにアクセスする[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="c57ee-117">You can use `CallByName` with classes in your current solution, but it is most often used to access COM objects or objects from [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies.</span></span>  
  
 <span data-ttu-id="c57ee-118">という名前のクラスを格納するアセンブリへの参照を追加すると仮定`MathClass`、という名前の新しい関数を持つ`SquareRoot`の次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c57ee-118">Suppose you add a reference to an assembly that contains a class named `MathClass`, which has a new function named `SquareRoot`, as shown in the following code:</span></span>  
  
 <span data-ttu-id="c57ee-119">[!code-vb[VbVbalrOOP #&53;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c57ee-119">[!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]</span></span>  
  
 <span data-ttu-id="c57ee-120">アプリケーションでは、コントロールのどのメソッドが呼び出されると、引数にテキスト ボックス コントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c57ee-120">Your application could use text box controls to control which method will be called and its arguments.</span></span> <span data-ttu-id="c57ee-121">たとえば場合、`TextBox1`に評価される式が含まれていて、`TextBox2`は関数の名前を入力するために使用を使えば、次のコードを呼び出す、`SquareRoot`で式に対して関数`TextBox1`:</span><span class="sxs-lookup"><span data-stu-id="c57ee-121">For example, if `TextBox1` contains the expression to be evaluated, and `TextBox2` is used to enter the name of the function, you can use the following code to invoke the `SquareRoot` function on the expression in `TextBox1`:</span></span>  
  
 <span data-ttu-id="c57ee-122">[!code-vb[VbVbalrOOP #&54;](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c57ee-122">[!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]</span></span>  
  
 <span data-ttu-id="c57ee-123">「64」を入力した場合`TextBox1`で"SquareRoot" `TextBox2`、しを呼び出す、`CallMath`プロシージャ、内の数値の平方根`TextBox1`が評価されます。</span><span class="sxs-lookup"><span data-stu-id="c57ee-123">If you enter "64" in `TextBox1`, "SquareRoot" in `TextBox2`, and then call the `CallMath` procedure, the square root of the number in `TextBox1` is evaluated.</span></span> <span data-ttu-id="c57ee-124">例のコードを呼び出す、 `SquareRoot` (必須の引数として評価される式を表す文字列を扱う) に機能し、「8」を返します`TextBox1`(の平方根 64)。</span><span class="sxs-lookup"><span data-stu-id="c57ee-124">The code in the example invokes the `SquareRoot` function (which takes a string that contains the expression to be evaluated as a required argument) and returns "8" in `TextBox1` (the square root of 64).</span></span> <span data-ttu-id="c57ee-125">もちろん、ユーザーが入力に無効な文字列`TextBox2`文字列に、メソッドの代わりにプロパティの名前が含まれているか、メソッドに追加の必須の引数がある場合、実行時エラーが発生した場合は、です。</span><span class="sxs-lookup"><span data-stu-id="c57ee-125">Of course, if the user enters an invalid string in `TextBox2`, if the string contains the name of a property instead of a method, or if the method had an additional required argument, a run-time error occurs.</span></span> <span data-ttu-id="c57ee-126">使用する場合は、堅牢なエラー処理コードを追加する必要がある`CallByName`これらやその他のエラーを予測します。</span><span class="sxs-lookup"><span data-stu-id="c57ee-126">You have to add robust error-handling code when you use `CallByName` to anticipate these or any other errors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c57ee-127">中に、`CallByName`関数がいくつかの場合に役立つこと、パフォーマンスに与える影響に対して有用性を比較検討する必要があります: を使用して`CallByName`プロシージャを呼び出すには、遅延バインディング呼び出しよりもわずかに低下します。</span><span class="sxs-lookup"><span data-stu-id="c57ee-127">While the `CallByName` function may be useful in some cases, you must weigh its usefulness against the performance implications — using `CallByName` to invoke a procedure is slightly slower than a late-bound call.</span></span> <span data-ttu-id="c57ee-128">呼び出される繰り返し、このようなループ内で、関数を呼び出す場合`CallByName`パフォーマンスに重大な影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="c57ee-128">If you are invoking a function that is called repeatedly, such as inside a loop, `CallByName` can have a severe effect on performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c57ee-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c57ee-129">See Also</span></span>  
 <span data-ttu-id="c57ee-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span><span class="sxs-lookup"><span data-stu-id="c57ee-130"><xref:Microsoft.VisualBasic.Interaction.CallByName%2A></span></span>   
<span data-ttu-id="c57ee-131"> [オブジェクトの型の決定](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span><span class="sxs-lookup"><span data-stu-id="c57ee-131"> [Determining Object Type](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)</span></span>
