---
title: "名前付き引数と省略可能な引数 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: "43"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e6fceb569a79b5988171f06ae6c09d86b5fc667d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>名前付き引数と省略可能な引数 (C# プログラミング ガイド)
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] では、名前付き引数と省略可能な引数が導入されています。 *名前付き引数*を使用すると、パラメーター リストのパラメーターの位置ではなく、パラメーター名に引数を関連付けることによって、特定のパラメーターの引数を指定できます。 *省略可能な引数*を使用すると、一部のパラメーターの引数を省略できます。 両方の手法をメソッド、インデクサー、コンストラクター、デリゲートで使用できます。  
  
 名前付き引数と省略可能な引数を使用すると、引数は、パラメーター リストではなく、引数リストに記述されている順に評価されます。  
  
 名前付きパラメーターと省略可能なパラメーターを併用する場合、省略可能なパラメーターのリストにあるパラメーターのうち、ごく一部のパラメーターに対してのみ引数を指定できます。 この機能により、Microsoft Office オートメーション API などの COM インターフェイスの呼び出しが大幅に円滑化します。  
  
## <a name="named-arguments"></a>名前付き引数  
 名前付き引数を使用すると、呼び出されたメソッドのパラメーター リストに記述されているパラメーターの順序を記憶したり、検索したりする必要がなくなります。 各引数のパラメーターはパラメーター名で指定できます。 たとえば、注文の詳細を出力する関数 (など、販売者名、注文数と製品名) 関数によって定義された順序で、位置による引数を送信することによって、標準の方法で呼び出すことができます。
  
 `PrintOrderDetails("Gift Shop", 31, "Red Mug");`
  
 パラメーターの順序を覚えていないの名前を把握する場合は、任意の順序で引数を送信することができます。  
  
 `PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");`
  
 `PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);`
  
 また、名前付き引数を使用すると、各引数が表すものが識別しやすくなり、コードが読みやすくなります。 次のメソッドの例で、 `sellerName` null または空白にすることはできません。 両方と`sellerName`と`productName`文字列型の場合は、位置による引数を送信する、代わりにすると良い名前付き引数を使用して、2 つのあいまいさを解消し、コードを読むすべてのユーザーの混乱を削減します。
  
 有効な名前付き引数の位置指定引数を使用すると、限り 

- 位置指定引数を受け取らず、している従わないまたは

 `PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");`

- _以降で c# 7.2_、正しい位置で使用されています。 次の例で、パラメーターで`orderNum`正しい位置にあるが、明示的に指定されていません。

 `PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");`
  
 ただし、順序不定な名前付き引数は、位置指定引数が続いている場合に有効ではありません。

 ```csharp
 // This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
 PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
 ```
  
## <a name="example"></a>例  
 次のコードでは、いくつかの追加機能と共に、このセクションの例を実装します。  
  
 [!code-csharp[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>省略可能な引数  
 メソッド、コンストラクター、インデクサー、デリゲートの定義では、そのパラメーターが必須であるか、省略可能であるかを指定できます。 どの呼び出しでも、すべての必須パラメーターに対して引数を指定する必要があります。ただし、省略可能なパラメーターの引数は省略できます。  
  
 省略可能な各パラメーターには、パラメーターの定義に既定値が含まれています。 そのパラメーターの引数を渡さない場合、既定値が使用されます。 既定値には、次のいずれかの種類の式を指定できます。  
  
-   定数式  
  
-   `new ValType()` 形式の式です。`ValType` は、[enum](../../../csharp/language-reference/keywords/enum.md) や [struct](../../../csharp/programming-guide/classes-and-structs/structs.md) のような値型になります。  
  
-   [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) 形式の式です。`ValType` は値型です。  
  
 省略可能なパラメーターは、パラメーター リストの末尾で必須パラメーターの後に定義されます。 呼び出し元は、連続する省略可能なパラメーターのいずれか 1 つに対して引数を指定する場合、先行するすべての省略可能なパラメーターに引数を指定する必要があります。 引数リストでは、スペースをコンマで区切ることはできません。 たとえば、次のコードでは、1 つの必須パラメーターと 2 つの省略可能パラメーターでインスタンス メソッド `ExampleMethod` が定義されます。  
  
 [!code-csharp[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 次に示す `ExampleMethod` の呼び出しでは、3 つ目のパラメーターに引数が指定されていますが、2 つ目のパラメーターには指定されていないため、コンパイル エラーが発生します。  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 ただし、3 つ目のパラメーターの名前がわかっている場合、名前付き引数を使用してタスクを実行できます。  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 次の例に示すように、IntelliSense では、省略可能なパラメーターを角かっこで示します。  
  
 ![ExampleMethod メソッドの IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
ExampleMethod の省略可能なパラメーター  
  
> [!NOTE]
>  また、.NET <xref:System.Runtime.InteropServices.OptionalAttribute> クラスを使用して省略可能なパラメーターを宣言することもできます。 `OptionalAttribute` パラメーターに既定値は必要ありません。  
  
## <a name="example"></a>例  
 次の例では、`ExampleClass` のコンストラクターに省略可能なパラメーターが 1 つあります。 `ExampleMethod` インスタンス メソッドには、`required` という 1 つの必須パラメーターと、`optionalstr` と `optionalint` という 2 つの省略可能なパラメーターがあります。 `Main` のコードに示すように、いくつかの異なる方法でコンストラクターとメソッドを呼び出すことができます。  
  
 [!code-csharp[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>COM インターフェイス  
 名前付き引数と省略可能な引数を動的オブジェクトやその他の拡張機能のサポートと併用すると、Office オートメーション API などの COM API との相互運用性が大幅に向上します。  
  
 たとえば、Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) インターフェイスの [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) メソッドには 7 つのパラメーターがあります。それらはすべて省略可能です。 これらのパラメーターを次の例に示します。  
  
 ![AutoFormat メソッドについての IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
AutoFormat パラメーター  
  
 C# 3.0 以前のバージョンの C# では、次の例に示すように、各パラメーターの引数が必要です。  
  
 [!code-csharp[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 ただし、C# 4.0 の導入により、名前付き引数と省略可能な引数を使用すると、`AutoFormat` の呼び出しを大幅に簡略化できます。 名前付き引数と省略可能な引数を使用すると、パラメーターの既定値の変更を望まない場合に、省略可能なパラメーターの引数を省略できます。 次の呼び出しでは、7 つのパラメーターのうちの 1 つのパラメーターのみに値を指定しています。  
  
 [!code-csharp[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 使用例を含む詳細については、「[方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)」と「[方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)」を参照してください。  
  
## <a name="overload-resolution"></a>Overload Resolution  
 名前付き引数と省略可能な引数を使用すると、オーバーロードの解決に次のように影響します。  
  
-   メソッド、インデクサー、コンストラクターのパラメーターのそれぞれが任意であるか、名前か位置により、呼び出しステートメントの 1 つの引数に対応するとき、その引数がパラメーターの型に変換できる場合、メソッド、インデクサー、コンストラクターが実行の候補になります。  
  
-   複数の候補が見つかった場合、明示的に指定される引数には、優先変換に関するオーバーロード解決の規則が適用されます。 任意のパラメーターの省略された引数は無視されます。  
  
-   2 つの候補が等しく良好であると判断された場合、呼び出しで引数が省略された任意のパラメーターのない候補が優先されます。 これはパラメーターの少ない候補に関するオーバーロード解決の一般優先設定の結果です。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)
