---
title: "enum (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 36
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f064ed0710a83e4bf0eaf5c35b962c29443f9d23
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="enum-c-reference"></a>enum (C# リファレンス)
`enum` キーワードは、列挙型を宣言するために使用されます。列挙型は、列挙子リストと呼ばれる名前付き定数の集まりで構成される固有の型です。  
  
 通常、列挙型は名前空間内に直接定義して、名前空間内のすべてのクラスが共通の利便性でアクセスできるようにするのが最も適切です。 ただし、列挙型はクラスまたは構造体内に入れ子にすることもできます。  
  
 既定では、最初の列挙子の値は 0 で、後続の列挙子の値は 1 ずつ増加していきます。 たとえば、次の列挙型では、 `Sat` は `0`、 `Sun` は `1`、 `Mon` は `2`などとなります。  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 列挙型では、次の例に示すように、初期化子を使用して既定値をオーバーライドできます。  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 この列挙型では、要素の並びは `1` からではなく、 `0`から開始します。 ただし、列挙型には値が 0 となる定数を含めておくことをお勧めします。 詳細については、[列挙型](../../../csharp/programming-guide/enumeration-types.md)を参照してください。  
  
 すべての列挙型には基になる型があり、基になる型には [char](../../../csharp/language-reference/keywords/char.md) 以外の任意の整数型を指定できます。 列挙要素の基になる既定の型は [int](../../../csharp/language-reference/keywords/int.md) です。 [byte](../../../csharp/language-reference/keywords/byte.md)など、他の整数型の列挙型を宣言するには、次の例に示すように、識別子に続けてコロンを使用し、その後に型を記述します。  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 列挙型で許容される型は、`byte`、[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) です。  
  
 型 `Days` の変数には、基になる型の範囲内の任意の値を割り当てることができます。値は名前付き定数に限定されません。  
  
 `enum E` の既定値は、式 `(E)0`によって算出された値です。  
  
> [!NOTE]
>  列挙子の名前に空白を使用することはできません。  
  
 基になる型は、列挙子ごとに割り当てるストレージの大きさを指定します。 ただし、 `enum` 型を整数型に変換するには、明示的なキャストが必要です。 たとえば、次のステートメントでは、キャストを使用して `enum` から `int` に変換することにより、列挙子 `Sun` を [int](../../../csharp/language-reference/keywords/int.md) 型の変数に代入します。  
  
```  
int x = (int)Days.Sun;  
```  
  
 列挙型に <xref:System.FlagsAttribute?displayProperty=fullName> を適用し、その要素をビットごとの `OR` 演算と組み合わせると、一部のツールを使用したときに、`enum` の動作に属性が反映されます。 このような変更は、<xref:System.Console> クラス メソッドや式エバリュエーターなどのツールを使用して確認できます。 (3 番目の使用例をご参照ください。)  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 定数の場合と同様に、列挙型の個々の値へのすべての参照はコンパイル時に数値リテラルに変換されます。 これにより、「[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)」で説明しているように、バージョン管理の問題が発生する可能性があります。  
  
 新しいバージョンの列挙型に追加の値を割り当てるか、新しいバージョンの列挙型メンバーの値を変更すると、依存関係のあるソース コードに問題が発生することがあります。 列挙値は、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでよく使用されます。 `enum` 型に追加要素が追加されている場合、switch ステートメントの default セクションが予期せずに選択される場合があります。  
  
 作成したコードが他の開発者によって使用される場合は、新しい要素を `enum` 型に追加したときのコードの反応を規定するガイドラインを用意しておく必要があります。  
  
## <a name="example"></a>例  
 次の例では、列挙型 `Days`を宣言しています。 2 つの列挙子は明示的に整数に変換され、整数変数に代入されます。  
  
 [!code-cs[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a>例  
 次の例では、基本型オプションを使用して `enum` 型をメンバーに持つ `long`を宣言しています。 列挙型の基になる型が `long`であっても、列挙型メンバーはキャストを使用して `long` 型に明示的に変換する必要があることにご注意ください。  
  
 [!code-cs[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a>例  
 次のコード例では、`enum` 宣言での <xref:System.FlagsAttribute?displayProperty=fullName> 属性の使用とその効果を示します。  
  
 [!code-cs[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a>コメント  
 この例では、 `Flags`を削除すると次の値が表示されます。  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [列挙型](../../../csharp/programming-guide/enumeration-types.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

