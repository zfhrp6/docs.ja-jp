---
title: "キャストと型変換 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 20743c07c8e9c6b7ec24cf52a28bb9f451ba9df5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="874f7-102">キャストと型変換 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="874f7-102">Casting and Type Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="874f7-103">C# はコンパイル時 (変数が宣言された後) に静的に型指定されるため、その型が変数の型に変換可能でない限り、再宣言したり、別の型の値を格納するために使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="874f7-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or used to store values of another type unless that type is convertible to the variable's type.</span></span> <span data-ttu-id="874f7-104">たとえば、整数から任意の文字列に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="874f7-104">For example, there is no conversion from an integer to any arbitrary string.</span></span> <span data-ttu-id="874f7-105">そのため、次のコードに示すように、`i` を整数として宣言した後、"Hello" という文字列を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="874f7-105">Therefore, after you declare `i` as an integer, you cannot assign the string "Hello" to it, as is shown in the following code.</span></span>  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 <span data-ttu-id="874f7-106">しかし場合によっては、別の型の変数やメソッドのパラメーターに値をコピーする必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="874f7-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="874f7-107">たとえば、パラメーターが `double` として型指定されたメソッドに、整数の変数を渡す必要が生じることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="874f7-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="874f7-108">また、クラス変数をインターフェイス型の変数に代入しなければならない場合もあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="874f7-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="874f7-109">この種の操作は、*型変換*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="874f7-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="874f7-110">C# では、次のような変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="874f7-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
-   <span data-ttu-id="874f7-111">**暗黙的な変換**: この変換はタイプ セーフであり、データが失われることはないため、特別な構文は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="874f7-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="874f7-112">例としては、小さい整数型から大きい整数型への変換や、派生クラスから基底クラスへの変換が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="874f7-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
-   <span data-ttu-id="874f7-113">**明示的な変換 (キャスト)**: 明示的な変換には、キャスト演算子が必要です。</span><span class="sxs-lookup"><span data-stu-id="874f7-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="874f7-114">変換時に情報が失われる可能性がある場合や、その他の理由によって変換が成功しない可能性がある場合には、キャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="874f7-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="874f7-115">典型的な例としては、より精度の低い型 (または、より範囲が狭い型) に数値を変換する場合や、基底クラスのインスタンスを派生クラスに変換する場合が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="874f7-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
-   <span data-ttu-id="874f7-116">**ユーザー定義の変換**: ユーザー定義の変換は、基本クラスと派生クラスの関係がないカスタム型の間で、明示的変換や暗黙的変換を実行できるようにするために定義する、特殊なメソッドによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="874f7-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="874f7-117">詳しくは、「[変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
-   <span data-ttu-id="874f7-118">**ヘルパー クラスを使用する変換**: 整数と <xref:System.DateTime?displayProperty=fullName> オブジェクトの間、16 進文字列とバイト配列の間など、互換性のない型の間で変換を行うには、<xref:System.BitConverter?displayProperty=fullName> クラス、<xref:System.Convert?displayProperty=fullName> クラス、および組み込み数値型の `Parse` メソッド (<xref:System.Int32.Parse%2A?displayProperty=fullName> など) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="874f7-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=fullName> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=fullName> class, the <xref:System.Convert?displayProperty=fullName> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="874f7-119">詳しくは、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、および「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="874f7-120">暗黙の型変換</span><span class="sxs-lookup"><span data-stu-id="874f7-120">Implicit Conversions</span></span>  
 <span data-ttu-id="874f7-121">組み込みの数値型の場合、格納される値を切り捨てたり丸めたりしなくても変数に収めることができるのであれば、暗黙的な変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="874f7-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="874f7-122">たとえば、[long](../../../csharp/language-reference/keywords/long.md) 型の変数 (8 バイトの整数) は、 [int](../../../csharp/language-reference/keywords/int.md) (32 ビット コンピューターでは 4 バイト) が格納できる任意の値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="874f7-122">For example, a variable of type [long](../../../csharp/language-reference/keywords/long.md) (8 byte integer) can store any value that an [int](../../../csharp/language-reference/keywords/int.md) (4 bytes on a 32-bit computer) can store.</span></span> <span data-ttu-id="874f7-123">次の例の場合、コンパイラは右側の値を `bigNum` に割り当てる前に、値を `long` 型へと暗黙的に変換します。</span><span class="sxs-lookup"><span data-stu-id="874f7-123">In the following example, the compiler implicitly converts the value on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 <span data-ttu-id="874f7-124">[!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="874f7-124">[!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]</span></span>  
  
 <span data-ttu-id="874f7-125">暗黙的な数値変換をすべてまとめた一覧については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-125">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="874f7-126">参照型の場合は、特定のクラスから、その直接または間接的な基底クラスやインターフェイスに対して、常に暗黙的な変換が存在します。</span><span class="sxs-lookup"><span data-stu-id="874f7-126">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="874f7-127">派生クラスには常に基底クラスのすべてのメンバーが含まれるため、特別な構文は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="874f7-127">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="874f7-128">明示的変換</span><span class="sxs-lookup"><span data-stu-id="874f7-128">Explicit Conversions</span></span>  
 <span data-ttu-id="874f7-129">変換によって情報が失われるリスクがある場合は、コンパイラで明示的な変換を実行する必要があります。これを*キャスト*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="874f7-129">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="874f7-130">キャストとは、変換を行う意図があることと、データ損失が発生する可能性があることを、コンパイラに明示的に知らせるための方法です。</span><span class="sxs-lookup"><span data-stu-id="874f7-130">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="874f7-131">キャストを実行するには、変換する値または変数の前に、キャストする型をかっこで囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="874f7-131">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="874f7-132">次のプログラでは、[double](../../../csharp/language-reference/keywords/double.md) を [int](../../../csharp/language-reference/keywords/int.md) にキャストしています。</span><span class="sxs-lookup"><span data-stu-id="874f7-132">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="874f7-133">このプログラムは、キャストなしではコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="874f7-133">The program will not compile without the cast.</span></span>  
  
 <span data-ttu-id="874f7-134">[!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="874f7-134">[!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]</span></span>  
  
 <span data-ttu-id="874f7-135">許可される明示的数値変換の一覧については、「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-135">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="874f7-136">参照型の場合は、基本型から派生型に変換する必要がある場合に、明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="874f7-136">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="874f7-137">参照型の間でキャスト操作を行っても、基になるオブジェクトの実行時の型は変わりません。そのオブジェクトへの参照として使用される値の型だけが変更されます。</span><span class="sxs-lookup"><span data-stu-id="874f7-137">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="874f7-138">詳しくは、「[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-138">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="874f7-139">実行時に発生する型変換の例外</span><span class="sxs-lookup"><span data-stu-id="874f7-139">Type Conversion Exceptions at Run Time</span></span>  
 <span data-ttu-id="874f7-140">一部の参照型変換では、キャストが有効になるかどうかをコンパイラで判断できません。</span><span class="sxs-lookup"><span data-stu-id="874f7-140">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="874f7-141">キャスト操作が正しくコンパイルされても、実行時に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="874f7-141">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="874f7-142">次の例に示すように、型キャストが実行時に失敗すると、<xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="874f7-142">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 <span data-ttu-id="874f7-143">[!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="874f7-143">[!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]</span></span>  
  
 <span data-ttu-id="874f7-144">C# では、キャストの実行前に互換性をテストできるよう、[is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が提供されています。</span><span class="sxs-lookup"><span data-stu-id="874f7-144">C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="874f7-145">詳しくは、「[方法: as 演算子と is 演算子を使用して安全にキャストする](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="874f7-145">For more information, see [How to: Safely Cast by Using as and is Operators](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="874f7-146">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="874f7-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="874f7-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="874f7-147">See Also</span></span>  
 <span data-ttu-id="874f7-148">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-148">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="874f7-149">[型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-149">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="874f7-150">[() 演算子](../../../csharp/language-reference/operators/invocation-operator.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-150">[() Operator](../../../csharp/language-reference/operators/invocation-operator.md) </span></span>  
 <span data-ttu-id="874f7-151">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-151">[explicit](../../../csharp/language-reference/keywords/explicit.md) </span></span>  
 <span data-ttu-id="874f7-152">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-152">[implicit](../../../csharp/language-reference/keywords/implicit.md) </span></span>  
 <span data-ttu-id="874f7-153">[変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span><span class="sxs-lookup"><span data-stu-id="874f7-153">[Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md) </span></span>  
 <span data-ttu-id="874f7-154">[一般的な型変換](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada) </span><span class="sxs-lookup"><span data-stu-id="874f7-154">[Generalized Type Conversion](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada) </span></span>  
 <span data-ttu-id="874f7-155">[エクスポート時の型の変換](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b) </span><span class="sxs-lookup"><span data-stu-id="874f7-155">[Exported Type Conversion](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b) </span></span>  
 [<span data-ttu-id="874f7-156">方法: 文字列を数値に変換する</span><span class="sxs-lookup"><span data-stu-id="874f7-156">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)

