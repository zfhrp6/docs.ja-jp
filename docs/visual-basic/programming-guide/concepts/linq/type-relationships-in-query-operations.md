---
title: "Type Relationships in Query Operations (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variable relationships [LINQ in Visual Basic]"
  - "type information inferred [LINQ in Visual Basic]"
  - "type relationships [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], type relationships"
  - "data sources [LINQ in Visual Basic], type relationships"
  - "LINQ [Visual Basic], type relationships"
  - "inferring type information [LINQ in Visual Basic]"
  - "relationships [LINQ in Visual Basic]"
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 32
---
# Type Relationships in Query Operations (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] クエリ操作で使用される変数は、厳密に型指定されていて、相互に互換性を持つ必要があります。  厳密な型指定は、データ ソース、クエリ自体、およびクエリの実行で使用されます。  次の図は、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリの説明で使用される用語を示しています。  クエリの各部分の詳細については、「[基本的なクエリ操作 \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)」を参照してください。  
  
 ![要素が強調表示された擬似コード クエリ。](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
LINQ クエリの各部分  
  
 クエリの範囲変数の型には、データ ソース内の要素の型との互換性が必要です。  クエリ変数の型には、`Select` 句で定義されるシーケンス要素との互換性が必要です。  さらに、シーケンス要素の型には、クエリを実行する `For Each` ステートメントで使用されているループ制御変数の型との互換性が必要です。  この厳密な型指定により、コンパイル時に型のエラーを特定しやすくなります。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、*暗黙の型指定*とも呼ばれるローカル型の推論が実装され、厳密な型指定を行いやすくなっています。  この機能は、前の例で使用されているほか、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] のサンプルおよびドキュメント全体にわたって使用されています。  Visual Basic では、単に `As` 句のない `Dim` ステートメントを使用することで、ローカル型の推論を適用させることができます。  次の例では、`city` は文字列として厳密に型指定されます。  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_1.vb)]  
  
> [!NOTE]
>  ローカル型の推論は、`Option Infer` が `On` に設定されているときにのみ機能します。  詳細については、「[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」を参照してください。  
  
 ただし、クエリでローカル型の推論を使用しても、データ ソース内の変数、クエリ変数、およびクエリの実行ループの間に同様の型の関係が存在します。  これらの型の関係の基本を理解しておくと、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを記述したり、このドキュメント内のサンプルやコード例を操作したりする場合に役立ちます。  
  
 場合によっては、データ ソースから返された型に一致しない範囲変数に対して、明示的な型を指定する必要が生じます。  `As` 句を使用することによって、範囲変数の型を指定できます。  ただし、`Option Strict` が `On` に設定されている場合に[縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)が行われると、エラーが発生する結果になります。  このため、データ ソースから取得された値に対して変換を実行することをお勧めします。  <xref:System.Linq.Enumerable.Cast%2A> メソッドを使用して、データ ソースの値を明示的な範囲変数の型に変換できます。  また、`Select` 句で選択された値を、範囲変数の型とは異なる明示的な型にキャストすることもできます。  これらの点を次のコードに示します。  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_2.vb)]  
  
## ソース データの要素全体を返すクエリ  
 次の例は、ソース データから選択された要素のシーケンスを返す [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリ操作を示しています。  ソースの `names` には文字列の配列が含まれ、クエリ出力は、文字 M から始まる文字列を含むシーケンスです。  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_3.vb)]  
  
 これは次のコードと同等ですが、より短く、簡単に記述できます。  Visual Basic では、ローカル型の推論に依存するスタイルでクエリを記述することをお勧めします。  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/visualbasic/type-relationships-in-qu_4.vb)]  
  
 型が暗黙的に決定されるか、または明示的に決定されるかに関係なく、前の両方のコード例には、次のような関係が存在します。  
  
1.  データ ソース `names` の要素の型は、クエリの範囲変数 `name` の型です。  
  
2.  選択されたオブジェクト `name` の型によって、クエリ変数 `mNames` の型が決まります。  この場合、`name` は文字列なので、クエリ変数は Visual Basic の IEnumerable\(Of String\) になります。  
  
3.  `mNames` で定義されるクエリは、`For Each` ループで実行されます。  ループによってクエリの実行結果が反復処理されます。  `mNames` は、実行されると文字列のシーケンスを返すので、ループの反復変数 `nm` も文字列です。  
  
## 選択した要素から 1 つのフィールドを返すクエリ  
 次の例は、データ ソースから選択された各要素の一部分のみを含むシーケンスを返す [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] クエリ操作を示しています。  このクエリは、データ ソースとして `Customer` オブジェクトのコレクションを受け取り、`Name` プロパティだけを結果に投影します。  顧客名は文字列なので、このクエリは文字列のシーケンスを出力として生成します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 変数間の関係は、より単純な最初の例の関係と同様です。  
  
1.  データ ソース `customers` の要素の型は、クエリの範囲変数 `cust` の型です。  この例では `Customer` 型です。  
  
2.  `Select` ステートメントは、オブジェクト全体ではなく、各 `Customer` オブジェクトの `Name` プロパティを返します。  `Name` は文字列なので、ここでもクエリ変数 `custNames` は IEnumerable\(Of String\) になり、`Customer` にはなりません。  
  
3.  `custNames` は文字列のシーケンスを表すので、`For Each` ループの反復変数 `custName` も文字列にする必要があります。  
  
 ローカル型の推論を使用しない場合、前の例は次のように記述できますが、作成するのも理解するのも面倒になります。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
## 匿名型を必要とするクエリ  
 次の例は、より複雑な状況を示しています。  前の例では、すべての変数に明示的に型を指定するのは面倒でも、不可能ではありませんでした。  この例では、それができません。  このクエリの `Select` 句は、データ ソースから `Customer` 要素全体を選択したり、各要素から単一のフィールドを選択したりする代わりに、元の `Customer` オブジェクトの 2 つのプロパティ、`Name` と `City` を返します。  `Select` 句に応答して、コンパイラはその 2 つのプロパティを含む匿名型を定義します。  `For Each` ループで `nameCityQuery` を実行すると、新しい匿名型のインスタンスのコレクションが返されます。  匿名型には使用できる名前がないため、`nameCityQuery` または `custInfo` の型を明示的に指定することはできません。  つまり、匿名型の場合、`IEnumerable(Of String)` の `String` の代わりに使用できる型名がありません。  詳細については、「[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 この例では、すべての変数に明示的に型を指定することはできませんが、関係は同じです。  
  
1.  データ ソース内の要素の型は、ここでも、クエリの範囲変数の型です。  この例では、`cust` は `Customer` のインスタンスです。  
  
2.  `Select` ステートメントによって匿名型が生成されるため、クエリ変数 `nameCityQuery` は、匿名型として暗黙的に型指定する必要があります。  匿名型には使用できる名前がないため、明示的に指定することはできません。  
  
3.  `For Each` ループの反復変数の型は、手順 2 で作成された匿名型になります。  この型には使用できる名前がないため、ループの反復変数の型は暗黙的に決定される必要があります。  
  
## 参照  
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)