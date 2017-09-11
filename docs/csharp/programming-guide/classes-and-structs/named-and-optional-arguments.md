---
title: "名前付き引数と省略可能な引数 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: a7f05e3e0b19bf6457989f8db2b46741cf6b28c1
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="28641-102">名前付き引数と省略可能な引数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="28641-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="28641-103"> では、名前付き引数と省略可能な引数が導入されています。</span><span class="sxs-lookup"><span data-stu-id="28641-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="28641-104">*名前付き引数*を使用すると、パラメーター リストのパラメーターの位置ではなく、パラメーター名に引数を関連付けることによって、特定のパラメーターの引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="28641-105">*省略可能な引数*を使用すると、一部のパラメーターの引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="28641-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="28641-106">両方の手法をメソッド、インデクサー、コンストラクター、デリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="28641-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="28641-107">名前付き引数と省略可能な引数を使用すると、引数は、パラメーター リストではなく、引数リストに記述されている順に評価されます。</span><span class="sxs-lookup"><span data-stu-id="28641-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="28641-108">名前付きパラメーターと省略可能なパラメーターを併用する場合、省略可能なパラメーターのリストにあるパラメーターのうち、ごく一部のパラメーターに対してのみ引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="28641-109">この機能により、Microsoft Office オートメーション API などの COM インターフェイスの呼び出しが大幅に円滑化します。</span><span class="sxs-lookup"><span data-stu-id="28641-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="28641-110">名前付き引数</span><span class="sxs-lookup"><span data-stu-id="28641-110">Named Arguments</span></span>  
 <span data-ttu-id="28641-111">名前付き引数を使用すると、呼び出されたメソッドのパラメーター リストに記述されているパラメーターの順序を記憶したり、検索したりする必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="28641-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="28641-112">各引数のパラメーターはパラメーター名で指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="28641-113">たとえば、肥満度指数 (BMI) を計算する関数は標準的な方法で呼び出すことができます。その関数で定義されている順序で、体重と身長の引数を位置によって渡します。</span><span class="sxs-lookup"><span data-stu-id="28641-113">For example, a function that calculates body mass index (BMI) can be called in the standard way by sending arguments for weight and height by position, in the order defined by the function.</span></span>  
  
 `CalculateBMI(123, 64);`  
  
 <span data-ttu-id="28641-114">パラメーターの順序を覚えていなくても、パラメーターの名前がわかっていれば、任意の順序で引数を渡すことができます。体重と身長のどちらを先にしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="28641-114">If you do not remember the order of the parameters but you do know their names, you can send the arguments in either order, weight first or height first.</span></span>  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 <span data-ttu-id="28641-115">また、名前付き引数を使用すると、各引数が表すものが識別しやすくなり、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="28641-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span>  
  
 <span data-ttu-id="28641-116">次に示すように、位置指定引数の後に続けて名前付き引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-116">A named argument can follow positional arguments, as shown here.</span></span>  
  
 `CalculateBMI(123, height: 64);`  
  
 <span data-ttu-id="28641-117">ただし、名前付き引数の後に位置指定引数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="28641-117">However, a positional argument cannot follow a named argument.</span></span> <span data-ttu-id="28641-118">次のステートメントはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="28641-118">The following statement causes a compiler error.</span></span>  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a><span data-ttu-id="28641-119">例</span><span class="sxs-lookup"><span data-stu-id="28641-119">Example</span></span>  
 <span data-ttu-id="28641-120">次のコードには、このセクションの例が実装されています。</span><span class="sxs-lookup"><span data-stu-id="28641-120">The following code implements the examples from this section.</span></span>  
  
 <span data-ttu-id="28641-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="28641-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span></span>  
  
## <a name="optional-arguments"></a><span data-ttu-id="28641-122">省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="28641-122">Optional Arguments</span></span>  
 <span data-ttu-id="28641-123">メソッド、コンストラクター、インデクサー、デリゲートの定義では、そのパラメーターが必須であるか、省略可能であるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-123">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="28641-124">どの呼び出しでも、すべての必須パラメーターに対して引数を指定する必要があります。ただし、省略可能なパラメーターの引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="28641-124">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="28641-125">省略可能な各パラメーターには、パラメーターの定義に既定値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="28641-125">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="28641-126">そのパラメーターの引数を渡さない場合、既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="28641-126">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="28641-127">既定値には、次のいずれかの種類の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="28641-127">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="28641-128">定数式</span><span class="sxs-lookup"><span data-stu-id="28641-128">a constant expression;</span></span>  
  
-   <span data-ttu-id="28641-129">`new ValType()` 形式の式です。`ValType` は、[enum](../../../csharp/language-reference/keywords/enum.md) や [struct](../../../csharp/programming-guide/classes-and-structs/structs.md) のような値型になります。</span><span class="sxs-lookup"><span data-stu-id="28641-129">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="28641-130">[default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) 形式の式です。`ValType` は値型です。</span><span class="sxs-lookup"><span data-stu-id="28641-130">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="28641-131">省略可能なパラメーターは、パラメーター リストの末尾で必須パラメーターの後に定義されます。</span><span class="sxs-lookup"><span data-stu-id="28641-131">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="28641-132">呼び出し元は、連続する省略可能なパラメーターのいずれか 1 つに対して引数を指定する場合、先行するすべての省略可能なパラメーターに引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28641-132">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="28641-133">引数リストでは、スペースをコンマで区切ることはできません。</span><span class="sxs-lookup"><span data-stu-id="28641-133">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="28641-134">たとえば、次のコードでは、1 つの必須パラメーターと 2 つの省略可能パラメーターでインスタンス メソッド `ExampleMethod` が定義されます。</span><span class="sxs-lookup"><span data-stu-id="28641-134">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 <span data-ttu-id="28641-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="28641-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="28641-136">次に示す `ExampleMethod` の呼び出しでは、3 つ目のパラメーターに引数が指定されていますが、2 つ目のパラメーターには指定されていないため、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="28641-136">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="28641-137">ただし、3 つ目のパラメーターの名前がわかっている場合、名前付き引数を使用してタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="28641-137">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="28641-138">次の例に示すように、IntelliSense では、省略可能なパラメーターを角かっこで示します。</span><span class="sxs-lookup"><span data-stu-id="28641-138">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="28641-139">![ExampleMethod メソッドの IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="28641-139">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="28641-140">ExampleMethod の省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="28641-140">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28641-141">また、.NET <xref:System.Runtime.InteropServices.OptionalAttribute> クラスを使用して省略可能なパラメーターを宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="28641-141">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="28641-142">`OptionalAttribute` パラメーターに既定値は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="28641-142">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28641-143">例</span><span class="sxs-lookup"><span data-stu-id="28641-143">Example</span></span>  
 <span data-ttu-id="28641-144">次の例では、`ExampleClass` のコンストラクターに省略可能なパラメーターが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="28641-144">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="28641-145">`ExampleMethod` インスタンス メソッドには、`required` という 1 つの必須パラメーターと、`optionalstr` と `optionalint` という 2 つの省略可能なパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="28641-145">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="28641-146">`Main` のコードに示すように、いくつかの異なる方法でコンストラクターとメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="28641-146">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 <span data-ttu-id="28641-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="28641-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span></span>  
  
## <a name="com-interfaces"></a><span data-ttu-id="28641-148">COM インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28641-148">COM Interfaces</span></span>  
 <span data-ttu-id="28641-149">名前付き引数と省略可能な引数を動的オブジェクトやその他の拡張機能のサポートと併用すると、Office オートメーション API などの COM API との相互運用性が大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="28641-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="28641-150">たとえば、Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) インターフェイスの [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) メソッドには 7 つのパラメーターがあります。それらはすべて省略可能です。</span><span class="sxs-lookup"><span data-stu-id="28641-150">For example, the [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) method in the Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="28641-151">これらのパラメーターを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="28641-151">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="28641-152">![AutoFormat メソッドについての IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="28641-152">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="28641-153">AutoFormat パラメーター</span><span class="sxs-lookup"><span data-stu-id="28641-153">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="28641-154">C# 3.0 以前のバージョンの C# では、次の例に示すように、各パラメーターの引数が必要です。</span><span class="sxs-lookup"><span data-stu-id="28641-154">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 <span data-ttu-id="28641-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="28641-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span></span>  
  
 <span data-ttu-id="28641-156">ただし、C# 4.0 の導入により、名前付き引数と省略可能な引数を使用すると、`AutoFormat` の呼び出しを大幅に簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="28641-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="28641-157">名前付き引数と省略可能な引数を使用すると、パラメーターの既定値の変更を望まない場合に、省略可能なパラメーターの引数を省略できます。</span><span class="sxs-lookup"><span data-stu-id="28641-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="28641-158">次の呼び出しでは、7 つのパラメーターのうちの 1 つのパラメーターのみに値を指定しています。</span><span class="sxs-lookup"><span data-stu-id="28641-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 <span data-ttu-id="28641-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="28641-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="28641-160">使用例を含む詳細については、「[方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)」と「[方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28641-160">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="28641-161">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="28641-161">Overload Resolution</span></span>  
 <span data-ttu-id="28641-162">名前付き引数と省略可能な引数を使用すると、オーバーロードの解決に次のように影響します。</span><span class="sxs-lookup"><span data-stu-id="28641-162">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="28641-163">メソッド、インデクサー、コンストラクターのパラメーターのそれぞれが任意であるか、名前か位置により、呼び出しステートメントの 1 つの引数に対応するとき、その引数がパラメーターの型に変換できる場合、メソッド、インデクサー、コンストラクターが実行の候補になります。</span><span class="sxs-lookup"><span data-stu-id="28641-163">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="28641-164">複数の候補が見つかった場合、明示的に指定される引数には、優先変換に関するオーバーロード解決の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="28641-164">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="28641-165">任意のパラメーターの省略された引数は無視されます。</span><span class="sxs-lookup"><span data-stu-id="28641-165">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="28641-166">2 つの候補が等しく良好であると判断された場合、呼び出しで引数が省略された任意のパラメーターのない候補が優先されます。</span><span class="sxs-lookup"><span data-stu-id="28641-166">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="28641-167">これはパラメーターの少ない候補に関するオーバーロード解決の一般優先設定の結果です。</span><span class="sxs-lookup"><span data-stu-id="28641-167">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="28641-168">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="28641-168">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="28641-169">関連項目</span><span class="sxs-lookup"><span data-stu-id="28641-169">See Also</span></span>  
 <span data-ttu-id="28641-170">[方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="28641-170">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="28641-171">[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="28641-171">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="28641-172">[コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="28641-172">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 [<span data-ttu-id="28641-173">インデクサーの使用</span><span class="sxs-lookup"><span data-stu-id="28641-173">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)

