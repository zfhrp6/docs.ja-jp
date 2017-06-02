---
title: "列挙型 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 7e33ed084c560470a486ebbb25035a59ddc18565
ms.openlocfilehash: 2014047f17f766023ba4db4981aad6e6d4902381
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="enumeration-types-c-programming-guide"></a>列挙型 (C# プログラミング ガイド)
列挙型 (列挙値または Enum とも呼ばれます) を利用すると、変数に割り当てる一連の名前付き整数定数を効率的に定義できます。 たとえば、値が週の曜日を表す変数を定義するとします。 その変数が格納するのは 7 つの意味のある値だけです。 これらの値を定義するために、列挙型を利用できます。列挙型は [enum](../../csharp/language-reference/keywords/enum.md) キーワードで宣言されます。  
  
 [!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]  
  
 既定では、列挙の各要素の基になる型は [int](../../csharp/language-reference/keywords/int.md) です。 前の例のように、コロンを使用し、別の整数型を指定できます。 使用可能な型の一覧については、「[enum (C# リファレンス)](../../csharp/language-reference/keywords/enum.md)」を参照してください。  
  
 次の例のように、基になる型に型変換することで、基になる数値を確認できます。  
  
```csharp  
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
  
 数値型ではなく列挙型を使用する利点を次に示します。  
  
-   変数に対して有効な値をクライアント コードのために明確に指定します。  
  
-   [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] の IntelliSense で、定義済みの値が一覧表示されます。  
  
 列挙子一覧に要素の値を指定しないとき、値は自動的に 1 ずつ増えます。 前の例では、`Days.Sunday` の値が 0 で、`Days.Monday` の値が 1 です。その後も同様に 1 ずつ増えます。 新しい `Days` オブジェクトを作成するとき、明示的に値を割り当てない場合、`Days.Sunday` の既定値 (0) が与えられます。 列挙を作成するときは、最も論理的な既定値を選択し、それにゼロの値を与えます。 それにより、列挙を作成したときに明示的に値を割り当てない場合、すべての列挙にその既定値が与えられます。  
  
 変数 `meetingDay` の型が `Days` の場合、(明示的な型変換なしで) `Days` により定義される値の 1 つのみを割り当てることができます。 会議の日が変更されたら、`Days` から `meetingDay` に新しい値を割り当てることができます。  
  
 [!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]  
  
> [!NOTE]
>  任意の整数値を `meetingDay` に割り当てることができます。 たとえば、`meetingDay = (Days) 42` というコード行はエラーを生成しません。 ただし、これは行わないでください。列挙変数は列挙により定義される値の 1 つのみを保持すると暗黙的に予想されるためです。 列挙型の変数に任意の値を割り当てると、エラーが発生する可能性が高くなります。  
  
 ある列挙型の列挙子一覧の要素に任意の値を割り当てることができます。また、計算された値を利用することもできます。  
  
 [!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]  
  
## <a name="enumeration-types-as-bit-flags"></a>ビット フラグとしての列挙型  
 列挙型を利用してビット フラグを定義できます。ビット フラグを定義すると、列挙型のインスタンスは列挙子一覧で定義されている値のあらゆる組み合わせを格納できます。 (もちろん、意味のない組み合わせやプログラム コードで許可されない組み合わせもあります。)  
  
 ビット フラグ列挙を作成するには、<xref:System.FlagsAttribute?displayProperty=fullName> 属性を適用し、ビット処理演算の `AND`、`OR`、`NOT`、`XOR` を実行できるように値を定義します。 ビット フラグ列挙に、"フラグが設定されていない" という意味のゼロの値を持つ名前付き定数を追加します。 "フラグが設定されていない" という意味ではない場合、ゼロの値をフラグに指定しないでください。  
  
 次の例では、`Days` 列挙の別のバージョンが定義されています。`Days2` という名前が付いています。 `Days2` に `Flags` 属性が与えられており、各値に次の大きい 2 の累乗が割り当てられています。 これにより、値が `Days2.Tuesday` と `Days2.Thursday` になる `Days2` 変数を作成できます。  
  
 [!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]  
  
 列挙にフラグを設定するには、次の例のように、ビット処理演算子 `OR` を利用します。  
  
 [!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]  
  
 特定のフラグが設定されているかどうかを判断するには、次の例のように、ビット処理演算 `AND` を利用します。  
  
 [!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]  
  
 <xref:System.FlagsAttribute?displayProperty=fullName> 属性を使用して列挙型を定義する際の検討事項の詳細については、<xref:System.Enum?displayProperty=fullName> に関する記事を参照してください。  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>System.Enum メソッドを利用して列挙値を検出し、操作する  
 列挙はすべて、<xref:System.Enum?displayProperty=fullName> 型のインスタンスです。 <xref:System.Enum?displayProperty=fullName> から新しいクラスを派生させることはできませんが、このメソッドを利用して列挙インスタンスの値に関する情報を検出し、操作できます。  
  
 [!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]  
  
 詳細については、「<xref:System.Enum?displayProperty=fullName>」を参照してください。  
  
 拡張メソッドを利用して列挙に新しいメソッドを作成することもできます。 詳細については、「[方法 : 列挙型対応の新しいメソッドを作成する](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)」を参照してください。  

## <a name="see-also"></a>関連項目  
 <xref:System.Enum?displayProperty=fullName>   
 [C# プログラミング ガイド](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)
