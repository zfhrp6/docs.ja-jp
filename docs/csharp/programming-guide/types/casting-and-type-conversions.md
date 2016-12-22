---
title: "キャストと型変換 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "キャスト [C#]"
  - "変換 [C#], 型"
  - "変換 (型を) [C#]"
  - "データ型変換 [C#]"
  - "数値変換 [C#]"
  - "型変換 [C#]"
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
caps.latest.revision: 52
caps.handback.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# キャストと型変換 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# はコンパイル時に静的に型指定されるため、変数を宣言した後、その型が他の変数の型に変換可能である場合を除き、再び宣言したり、他の型の値の格納に使用したりすることはできません。  たとえば、整数から任意の文字列に変換することはできません。  したがって、次のコードに示すように、`i` を整数として宣言した後に、"Hello" という文字列を割り当てることはできません。  
  
```c#  
int i;  
i = "Hello"; // Error: "Cannot implicitly convert type 'string' to 'int'"  
```  
  
 ただし、値を別の型の変数やメソッド パラメーターにコピーする必要がある場合があります。  たとえば、パラメーターが `double` として型指定されているメソッドに整数変数を渡す必要がある場合があります。  または、インターフェイス型の変数にクラス変数を割り当てる必要がある場合もあります。  この種の操作は*型変換*と呼ばれます。  C\# では、次の種類の変換を実行できます。  
  
-   **暗黙の型変換** : 変換はタイプ セーフであり、データが失われることはないため、特別な構文は不要です。  たとえば、小さい整数型から大きい整数型に変換したり、派生クラスから基本クラスに変換したりする場合です。  
  
-   **明示的な型変換 \(キャスト\)** : 明示的な型変換にはキャスト演算子が必要です。  キャストが必要になるのは、変換時に情報が失われる可能性があるとき、または他の理由により変換が成功しないときです。典型的な例としては、精度の低い型または範囲の狭い型への数値変換や、基本クラス インスタンスの派生クラスへの変換があります。  
  
-   **ユーザー定義変換** : ユーザー定義変換は、基本クラスと派生クラスの関係がないカスタム型の間で、明示的な型変換と暗黙の型変換を有効にするために定義できる特別なメソッドによって実行されます。  詳細については、「[変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)」を参照してください。  
  
-   **ヘルパー クラスを使用した変換** : 整数と <xref:System.DateTime?displayProperty=fullName> オブジェクト、16 進文字列とバイト配列など、互換性のない型の間で変換を行うには、<xref:System.BitConverter?displayProperty=fullName> クラス、<xref:System.Convert?displayProperty=fullName> クラス、組み込みの数値型の `Parse` メソッド \(<xref:System.Int32.Parse%2A?displayProperty=fullName> など\) を使用できます。  詳細については、「[方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)」、「[方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)」、および「[方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)」を参照してください。  
  
## 暗黙の型変換  
 組み込みの数値型では、格納する値を切り捨てたり丸めたりしなくても変数に格納できる場合、暗黙の型変換を行うことができます。  たとえば、[long](../../../csharp/language-reference/keywords/long.md) 型 \(8 バイト整数\) の変数には、[int](../../../csharp/language-reference/keywords/int.md) \(32 ビット コンピューター上の 4 バイト\) に格納できるどの値でも格納できます。  次の例では、コンパイラは、右側の値を `long` 型に暗黙的に変換してから `bigNum` に代入しています。  
  
 [!code-cs[csProgGuideTypes#34](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_1.cs)]  
  
 暗黙の数値変換の一覧については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。  
  
 参照型の場合、あるクラスから、その直接基本クラスまたは間接基本クラスやインターフェイスへの暗黙的な変換が常に存在します。  派生クラスには基本クラスのすべてのメンバーが常に含まれるため、特別な構文は不要です。  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## 明示的な変換  
 ただし、変換により情報を失う可能性がある場合、コンパイラにより*キャスト*と呼ばれる明示的な変換を実行することが要求されます。  キャストは、ユーザーが変換を行うこと、およびデータ損失の可能性を認識していることをコンパイラに明示的に通知する方法です。  キャストを実行するには、変換される値または変数の前のかっこ内にキャストする型を指定します。  次のプログラムは、[double](../../../csharp/language-reference/keywords/double.md) を [int](../../../csharp/language-reference/keywords/int.md) にキャストします。  このプログラムは、キャストしないとコンパイルできません。  
  
 [!code-cs[csProgGuideTypes#2](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_2.cs)]  
  
 許可される明示的な数値変換の一覧については、「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」を参照してください。  
  
 参照型では、基本型から派生型に変換する必要がある場合、明示的なキャストが必要です。  
  
```c#  
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
  
 参照型間のキャスト操作では、基になるオブジェクトのランタイム型は変わらず、そのオブジェクトへの参照として使用される値の型だけが変わります。  詳細については、「[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)」を参照してください。  
  
## 実行時の型変換の例外  
 一部の参照型変換では、コンパイラはキャストが有効になるかどうかを判断できません。  正常にコンパイルされるキャスト操作が、実行時に失敗する可能性があります。  次の例に示すように、実行時に失敗する型キャストにより、<xref:System.InvalidCastException> がスローされます。  
  
 [!code-cs[csProgGuideTypes#41](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/casting-and-type-conversions_3.cs)]  
  
 C\# には [is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が用意されており、実際にキャストを実行する前に互換性をテストできます。  詳細については、「[方法: as 演算子と is 演算子を使用して安全にキャストする](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参考書籍の該当する章  
 [More About Variables](http://go.microsoft.com/fwlink/?LinkId=221230) 入力 [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\(\) 演算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [explicit](../../../csharp/language-reference/keywords/explicit.md)   
 [implicit](../../../csharp/language-reference/keywords/implicit.md)   
 [変換演算子](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)   
 [Generalized Type Conversion](../Topic/Generalized%20Type%20Conversion.md)   
 [Exported Type Conversion](http://msdn.microsoft.com/ja-jp/1dfe55f4-07a2-4b61-aabf-a8cf65783a6b)   
 [方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)