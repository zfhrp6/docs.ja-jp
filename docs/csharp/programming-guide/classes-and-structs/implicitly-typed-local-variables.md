---
title: "暗黙的に型指定されたローカル変数 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: 23
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 59bb61d8dd530e87f342d38acb131fab5e25febf
ms.lasthandoff: 03/13/2017

---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>暗黙的に型指定されるローカル変数 (C# プログラミング ガイド)
ローカル変数には、明示的な型の代わりに、推論される "型" `var` を指定できます。 `var` キーワードは、初期化ステートメントの右辺にある式から変数の型を推論するようにコンパイラに指示します。 推論される型は、組み込み型、匿名型、ユーザー定義型、または .NET Framework クラス ライブラリで定義されている型である可能性があります。 `var` で配列を初期化する方法の詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
 ローカル変数を `var` で宣言するさまざまな方法を次の例に示します。  
  
 [!code-cs[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 `var` キーワードは "バリアント" を意味するのではなく、変数の厳密でない型指定や遅延バインディングを示すものでもないことを理解することが重要です。 単に、最も適切な型をコンパイラが決定して割り当てることを意味します。  
  
 `var` キーワードは、次のコンテキストで使用される場合があります。  
  
-   前の例で示したようなローカル変数 (メソッドのスコープで宣言された変数)。  
  
-   [for](../../../csharp/language-reference/keywords/for.md) 初期化ステートメント。  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 初期化ステートメント。  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   [using](../../../csharp/language-reference/keywords/using-statement.md) ステートメント。  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 詳細については、「[方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)」を参照してください。  
  
## <a name="var-and-anonymous-types"></a>var と匿名型  
 多くの場合、`var` の使用は任意であり、構文上便利なだけです。 ただし、変数が匿名型で初期化される場合、後でオブジェクトのプロパティへのアクセスが必要になったら、変数を `var` として宣言する必要があります。 これは、[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] クエリ式では一般的なシナリオです。 詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
 ソース コードの観点から見ると、匿名型には名前がありません。 そのため、クエリ変数が `var` で初期化された場合、返されたオブジェクトのシーケンスのプロパティにアクセスするための唯一の方法は、`foreach` ステートメント内の繰り返し変数の型として `var` を使用することです。  
  
 [!code-cs[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a>コメント  
 暗黙的に型指定される変数の宣言には、次の制限が適用されます。  
  
-   `var` を使用できるのは、同じステートメント内でローカル変数の宣言と初期化が行われる場合のみです。この変数は、null、メソッド グループ、または匿名関数に初期化することはできません。  
  
-   `var` は、クラス スコープのフィールドで使用できません。  
  
-   `var` を使用して宣言された変数は、初期化式では使用できません。 つまり、`: int i = (i = 20);` という式は有効ですが、`var i = (i = 20);` という式はコンパイル時のエラーを生成します。  
  
-   暗黙的に型指定された複数の変数を同じステートメント内で初期化することはできません。  
  
-   `var` という名前の型がスコープ内にある場合、`var` キーワードはその型名に解決され、暗黙的に型指定されたローカル変数の宣言の一部とは見なされません。  
  
 `var` は、クエリ式と使用する場合に便利なこともあります。クエリ変数の構築された型を厳密に判別することが難しい場合です。 このような状況は、グループ化と並べ替えの処理で発生することがあります。  
  
 `var` キーワードは、変数の特定の型をキーボードで入力するのが面倒な場合、その型が明白な場合、型によってコードが読みやすくならない場合にも役立ちます。 このような理由で `var` が有用な例の 1 つとして、グループ化処理で使用されるような入れ子にされたジェネリック型があります。 次のクエリでは、クエリ変数の型は `IEnumerable<IGrouping<string, Student>>` です。 コードの作成者とそのコードを保守する担当者がこの点を理解している限り、簡略化するために暗黙的な型指定を使用しても問題はありません。  
  
 [!code-cs[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 ただし、`var` を使用すると、他の開発者がコードを理解しづらくなる可能性はあります。 このため、C# のドキュメントでは、通常、必要な場合にだけ `var` を使用しています。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)   
 [方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [LINQ (統合言語クエリ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)   
 [for](../../../csharp/language-reference/keywords/for.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)
