---
title: "名前付き引数と省略可能な引数 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "namedParameter_CSharpKeyword"
  - "cs_namedParameter"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "引数 [C#], 名前付き"
  - "引数 [C#], optional"
  - "名前付き引数と省略可能な引数 [C#]"
  - "名前付き引数 [C#]"
  - "省略可能な引数 [C#]"
  - "パラメーター [C#], 名前付き"
  - "パラメーター [C#], optional"
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 名前付き引数と省略可能な引数 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] では名前付き引数と省略可能な引数が導入されています。  *名前付き引数*を使用すると、パラメーター リストのパラメーターの位置ではなく、パラメーター名に引数を関連付けることによって、特定のパラメーターの引数を指定できます。  *省略可能な引数*を使用すると、一部のパラメーターの引数を省略できます。   両方の手法をメソッド、インデクサー、コンストラクター、およびデリゲートで使用できます。  
  
 名前付き引数および省略可能な引数を使用すると、引数は、パラメーター リストではなく引数リストに記述されている順に評価されます。  
  
 名前付きパラメーターと省略可能なパラメーターを併用する場合、省略可能なパラメーターのリストにあるパラメーターのうち、少数のパラメーターに対してのみ引数を指定できます。  この機能によって、Microsoft Office オートメーション API などの COM インターフェイスの呼び出しが大幅に簡易化します。  
  
## 名前付き引数  
 名前付き引数を使用すると、呼び出されたメソッドのパラメーター リストに記述されているパラメーターの順序を記憶したり、検索したりする必要がありません。  各引数のパラメーターはパラメーター名で指定できます。  たとえば、肥満度指数 \(BMI\) を計算する関数は、この関数で定義している順序で体重および身長の引数を位置によって渡す標準的な方法で、呼び出すことができます。  
  
 `CalculateBMI(123, 64);`  
  
 しかし、パラメーターの順序を覚えていなくても、パラメーターの名前がわかっていれば、1 番目のパラメーターとして体重または身長のどちらを指定してもよく、任意の順序で引数を渡すことができます。  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 また、名前付き引数を使用すると、各引数が何を表すかがわかるのでコードが読みやすくなります。  
  
 次に示すように、位置指定引数の後に続けて名前付き引数を指定できます。  
  
 `CalculateBMI(123, height: 64);`  
  
 ただし、位置指定引数を名前付き引数の後に続けて指定することはできません。  次のステートメントはコンパイラ エラーになります。  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## 例  
 次のコードには、このセクションの例が実装されています。  
  
 [!CODE [csProgGuideNamedAndOptional#1](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#1)]  
  
## 省略可能な引数  
 メソッド、コンストラクター、インデクサー、またはデリゲートの定義では、そのパラメーターが必須であるか、省略可能であるかを指定できます。  どの呼び出しでも、すべての必須パラメーターに対して引数を指定する必要があります。ただし、省略可能なパラメーターの引数は省略できます。  
  
 省略可能な各パラメーターの場合、パラメーターの定義に既定値が含まれています。  そのパラメーターの引数を渡さない場合は、既定値が使用されます。  既定値は式の種類の 1 種類があります :  
  
-   定数式 ;  
  
-   `ValType` は値型である [列挙](../../../csharp/language-reference/keywords/enum.md) または [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md) のような形式の式 `new ValType()`;  
  
-   `ValType` は値型であるフォーム [既定値 \(\) ValType](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md) の表現。  
  
 省略可能なパラメーターは、パラメーター リストの末尾で必須パラメーターの後に定義されます。  呼び出し元は、連続する省略可能なパラメーターのいずれか 1 つに対して引数を指定する場合、前にあるすべての省略可能なパラメーターに引数を指定する必要があります。   引数リストでコンマ区切りのスペースはサポートされていません。  たとえば、次のコードでは、1 つの必須パラメーターと 2 つの省略可能なパラメーターでインスタンス メソッド `ExampleMethod` が定義されます。  
  
 [!CODE [csProgGuideNamedAndOptional#15](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#15)]  
  
 次に示す `ExampleMethod` の呼び出しでは、3 番目のパラメーターに引数が指定されていますが、2 番目のパラメーターには指定されていないため、コンパイル エラーが発生します。  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 ただし、3 番目のパラメーターの名前がわかっている場合は、名前付き引数を使用して処理を実行できます。  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 次の例に示すように、IntelliSense では、省略可能なパラメーターを角かっこで示します。  
  
 ![ExampleMethod メソッドの IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional\_Parameters")  
ExampleMethod の省略可能なパラメーター  
  
> [!NOTE]
>  また、.NET <xref:System.Runtime.InteropServices.OptionalAttribute> クラスを使用して省略可能なパラメーターを宣言することもできます。  `OptionalAttribute` パラメーターに既定値は必要ありません。  
  
## 例  
 次の例では、`ExampleClass` のコンストラクターに省略可能なパラメーターが 1 つあります。  `ExampleMethod` インスタンス メソッドには、`required` という 1 つの必須パラメーターと、`optionalstr` および `optionalint` という 2 つの省略可能なパラメーターがあります。  `Main` のコードに示すように、いくつかの異なる方法でコンストラクターとメソッドを呼び出すことができます。  
  
 [!CODE [csProgGuideNamedAndOptional#2](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#2)]  
  
## COM インターフェイス  
 名前付き引数と省略可能な引数を動的オブジェクトやその他の拡張機能のサポートと併用すると、Office オートメーション API などの COM API との相互運用性が向上します。  
  
 たとえば、Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) インターフェイスの [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) メソッドには 7 つのパラメーターがあります。それらはすべて省略可能です。  これらのパラメーターを次の例に示します。  
  
 ![AutoFormat メソッドについての IntelliSense によるクイック ヒント](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat\_Parameters")  
AutoFormat のパラメーター  
  
 C\# 3.0 および旧バージョンの C\# では、次の例に示すように、各パラメーターの引数が必要です。  
  
 [!CODE [csProgGuideNamedAndOptional#3](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#3)]  
  
 しかし、C\# 4.0 の導入により、名前付き引数と省略可能な引数を使用すると、`AutoFormat` の呼び出しを大幅に簡略化できます。  名前付き引数と省略可能な引数を使用すると、パラメーターの既定値の変更を望まない場合に、省略可能なパラメーターの引数を省略できます。  次の呼び出しでは、7 つのパラメーターのうち 1 つのパラメーターのみに値を指定しています。  
  
 [!CODE [csProgGuideNamedAndOptional#13](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#13)]  
  
 使用例を含む詳細については、「[方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)」および「[方法: Visual C\# の機能を使用して Office 相互運用オブジェクトにアクセスする](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
## オーバーロードの解決法  
 名前付き引数と省略可能な引数を使用すると、オーバーロードの解決に次のように影響します。  
  
-   メソッド、インデクサー、またはコンストラクターの各パラメーターが省略可能である場合、または呼び出し側ステートメントの 1 つの引数に名前または位置によって対応し、その引数をパラメーターの型に変換できる場合、そのメソッド、インデクサー、またはコンストラクターは実行の候補となります。  
  
-   複数の候補が見つかった場合は、明示的に指定されている引数に対して、優先される変換のオーバーロードの解決規則が適用されます。  省略可能なパラメーターの省略された引数は無視されます。  
  
-   2 つの候補が同等である場合は、呼び出しで引数が省略された省略可能なパラメーターを持たない候補が優先されます。  これは、比較的少ないパラメーターを持つ候補のオーバーロードの解決での一般的な優先順に従った結果です。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [コンストラクターの使用](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [インデクサーの使用](../../../csharp/programming-guide/indexers/using-indexers.md)