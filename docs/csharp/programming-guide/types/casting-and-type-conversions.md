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
# <a name="casting-and-type-conversions-c-programming-guide"></a>キャストと型変換 (C# プログラミング ガイド)
C# はコンパイル時 (変数が宣言された後) に静的に型指定されるため、その型が変数の型に変換可能でない限り、再宣言したり、別の型の値を格納するために使用することはできません。 たとえば、整数から任意の文字列に変換することはできません。 そのため、次のコードに示すように、`i` を整数として宣言した後、"Hello" という文字列を割り当てることはできません。  
  
```csharp  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 しかし場合によっては、別の型の変数やメソッドのパラメーターに値をコピーする必要が生じることもあります。 たとえば、パラメーターが `double` として型指定されたメソッドに、整数の変数を渡す必要が生じることもあるでしょう。 また、クラス変数をインターフェイス型の変数に代入しなければならない場合もあるかもしれません。 この種の操作は、*型変換*と呼ばれます。 C# では、次のような変換を実行できます。  
  
-   **暗黙的な変換**: この変換はタイプ セーフであり、データが失われることはないため、特別な構文は必要ありません。 例としては、小さい整数型から大きい整数型への変換や、派生クラスから基底クラスへの変換が挙げられます。  
  
-   **明示的な変換 (キャスト)**: 明示的な変換には、キャスト演算子が必要です。 変換時に情報が失われる可能性がある場合や、その他の理由によって変換が成功しない可能性がある場合には、キャストが必要です。  典型的な例としては、より精度の低い型 (または、より範囲が狭い型) に数値を変換する場合や、基底クラスのインスタンスを派生クラスに変換する場合が挙げられます。  
  
-   **ユーザー定義の変換**: ユーザー定義の変換は、基本クラスと派生クラスの関係がないカスタム型の間で、明示的変換や暗黙的変換を実行できるようにするために定義する、特殊なメソッドによって実行されます。 詳しくは、「[変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)」をご覧ください。  
  
-   **ヘルパー クラスを使用する変換**: 整数と <xref:System.DateTime?displayProperty=fullName> オブジェクトの間、16 進文字列とバイト配列の間など、互換性のない型の間で変換を行うには、<xref:System.BitConverter?displayProperty=fullName> クラス、<xref:System.Convert?displayProperty=fullName> クラス、および組み込み数値型の `Parse` メソッド (<xref:System.Int32.Parse%2A?displayProperty=fullName> など) を使用できます。 詳しくは、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、および「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」をご覧ください。  
  
## <a name="implicit-conversions"></a>暗黙の型変換  
 組み込みの数値型の場合、格納される値を切り捨てたり丸めたりしなくても変数に収めることができるのであれば、暗黙的な変換を実行できます。 たとえば、[long](../../../csharp/language-reference/keywords/long.md) 型の変数 (8 バイトの整数) は、 [int](../../../csharp/language-reference/keywords/int.md) (32 ビット コンピューターでは 4 バイト) が格納できる任意の値を格納できます。 次の例の場合、コンパイラは右側の値を `bigNum` に割り当てる前に、値を `long` 型へと暗黙的に変換します。  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 暗黙的な数値変換をすべてまとめた一覧については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。  
  
 参照型の場合は、特定のクラスから、その直接または間接的な基底クラスやインターフェイスに対して、常に暗黙的な変換が存在します。 派生クラスには常に基底クラスのすべてのメンバーが含まれるため、特別な構文は必要ありません。  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a>明示的変換  
 変換によって情報が失われるリスクがある場合は、コンパイラで明示的な変換を実行する必要があります。これを*キャスト*と呼びます。 キャストとは、変換を行う意図があることと、データ損失が発生する可能性があることを、コンパイラに明示的に知らせるための方法です。 キャストを実行するには、変換する値または変数の前に、キャストする型をかっこで囲んで指定します。 次のプログラでは、[double](../../../csharp/language-reference/keywords/double.md) を [int](../../../csharp/language-reference/keywords/int.md) にキャストしています。 このプログラムは、キャストなしではコンパイルされません。  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 許可される明示的数値変換の一覧については、「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」をご覧ください。  
  
 参照型の場合は、基本型から派生型に変換する必要がある場合に、明示的なキャストが必要です。  
  
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
  
 参照型の間でキャスト操作を行っても、基になるオブジェクトの実行時の型は変わりません。そのオブジェクトへの参照として使用される値の型だけが変更されます。 詳しくは、「[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)」をご覧ください。  
  
## <a name="type-conversion-exceptions-at-run-time"></a>実行時に発生する型変換の例外  
 一部の参照型変換では、キャストが有効になるかどうかをコンパイラで判断できません。 キャスト操作が正しくコンパイルされても、実行時に失敗する可能性があります。 次の例に示すように、型キャストが実行時に失敗すると、<xref:System.InvalidCastException> がスローされます。  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C# では、キャストの実行前に互換性をテストできるよう、[is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が提供されています。 詳しくは、「[方法: as 演算子と is 演算子を使用して安全にキャストする](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)」をご覧ください。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [() 演算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [一般的な型変換](http://msdn.microsoft.com/library/49253ae6-7657-4810-82ab-1176a6feeada)   
 [エクスポート時の型の変換](http://msdn.microsoft.com/en-us/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)

