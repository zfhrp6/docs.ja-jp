---
title: "列挙型 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ビット フラグ [C#]"
  - "C# 言語, 列挙型"
  - "列挙型 [C#]"
  - "列挙型 [C#]"
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# 列挙型 (C# プログラミング ガイド)
列挙型 \(列挙値または Enum と呼ばれることもあります\) により、変数に割り当てられる一連の名前付きの整数定数を効率的に定義できます。  たとえば、値が曜日を表す変数を定義する必要があるとします。  その変数が格納する有意な値は 7 つのみです。  列挙型を使用してそれらの値を定義できます。列挙型は [enum](../../csharp/language-reference/keywords/enum.md) キーワードを使用して定義されます。  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_1.cs)]  
  
 既定では、列挙型の各要素の基になる型は [int](../../csharp/language-reference/keywords/int.md) です。  前の例に示したように、コロンを使用することで、別の整数型を指定できます。  使用可能なすべての型の一覧については、「[enum \(C\# リファレンス\)](../../csharp/language-reference/keywords/enum.md)」を参照してください。  
  
 基になる型にキャストして、基になる数値を確認するには、次の例に示すよう。  
  
```c#  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 数値型ではなく列挙型を使用する利点は次のとおりです。  
  
-   変数に対して有効な値をクライアント コードとして明確に指定します。  
  
-   [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)] では、IntelliSense によって定義済みの値が一覧表示されます。  
  
 列挙子リストで要素の値を指定しない場合、値は自動的に 1 ずつインクリメントされます。  前の例では、`Days.Sunday` の値は 0、`Days.Monday` の値は 1 のようになります。  新しい `Days` オブジェクトを作成し、値を明示的に割り当てない場合、既定値は `Days.Sunday` \(0\) になります。  列挙型を作成するときに、最も論理的な既定値を選択し、値 0 を割り当てます。  これにより、作成時に値が明示的に割り当てられない場合でも、すべての列挙型にその既定値が設定されます。  
  
 変数 `meetingDay` が `Days` 型の場合、\(明示的なキャストを使用せずに\) 割り当てることができるのは、`Days` で定義されている値の 1 つのみです。  ミーティングの日が変更された場合は、`Days` から `meetingDay` に新しい値を割り当てることができます。  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  `meetingDay` には任意の整数値を割り当てることができます。  たとえば、コード行 `meetingDay = (Days) 42` ではエラーは発生しません。  ただし、列挙型変数は列挙型で定義されている値の 1 つのみを保持すると暗黙的に予想されるため、これは実行しないでください。  列挙型の変数に任意の値を割り当てると、エラーが発生する可能性が高くなります。  
  
 列挙型の列挙子リストの要素に任意の値を割り当て、計算値として使用することもできます。  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_3.cs)]  
  
## ビット フラグとしての列挙型  
 列挙型を使用してビット フラグを定義できます。これにより、列挙型のインスタンスは、列挙子リストで定義されている値の任意の組み合わせを格納できます   \(ただし、プログラム コードで意味を持たない、または許可されない組み合わせも存在します\)。  
  
 <xref:System.FlagsAttribute?displayProperty=fullName> 属性を適用し、`AND`、`OR`、`NOT`、および `XOR` の各ビット処理演算子が実行されるように値を適切に定義することで、ビット フラグ列挙体を作成できます。  ビット フラグ列挙体に、値が 0 \("フラグが設定されていない" ことを意味します\) の名前付き定数を含めます。"フラグが設定されていない" ことを意味しない場合は、フラグに値 0 を指定しないでください。  
  
 次の例では、`Days2` という名前の別のバージョンの `Days` 列挙型を定義しています。  `Days2` は `Flags` 属性を持ち、それぞれの値には次に大きい 2 の累乗が割り当てられます。  これにより、値が `Days2` および `Days2.Tuesday` である `Days2.Thursday` 変数を作成できます。  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_4.cs)]  
  
 列挙型でフラグを設定するには、次の例に示すように、ビットごとの `OR` 演算子を使用します。  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_5.cs)]  
  
 特定のフラグが設定されているかどうかを確認するには、次の例に示すように、ビットごとの `AND` 演算子を使用します。  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_6.cs)]  
  
 <xref:System.FlagsAttribute?displayProperty=fullName> 属性を使用して列挙型を定義するときに考慮する内容の詳細については、「<xref:System.Enum?displayProperty=fullName>」を参照してください。  
  
## System.Enum メソッドを使用した列挙値の検出と操作  
 列挙値はすべて <xref:System.Enum?displayProperty=fullName> 型のインスタンスです。  <xref:System.Enum?displayProperty=fullName> から新しいクラスを派生させることはできませんが、そのメソッドを使用して、列挙定数インスタンスの値に関する情報を検出し、その値を操作できます。  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/csharp/enumeration-types_7.cs)]  
  
 詳細については、「<xref:System.Enum?displayProperty=fullName>」を参照してください。  
  
 拡張メソッドを使用して、列挙型の新しいメソッドを作成することもできます。  詳細については、「[方法 : 列挙型対応の新しいメソッドを作成する](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)」を参照してください。  
  
## 参考書籍の該当する章  
 [変数に関する詳細](http://go.microsoft.com/fwlink/?LinkId=221230) [先頭 Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## 参照  
 <xref:System.Enum?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)