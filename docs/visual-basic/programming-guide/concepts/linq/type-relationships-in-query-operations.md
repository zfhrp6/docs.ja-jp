---
title: クエリ操作での型の関係 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: ed0072eeb44a17201ddab2af6f6a44fd14461029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655343"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>クエリ操作での型の関係 (Visual Basic)
使用される変数[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ操作は、厳密に型指定し、相互に互換性がある必要があります。 厳密な型指定は、データ ソース、クエリ自体、およびクエリの実行に使用されます。 次の図は、説明に使用される用語の識別、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 クエリの部分についての詳細については、次を参照してください。[基本的なクエリ操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)です。  
  
 ![要素が強調表示された擬似コード クエリ。] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")  
LINQ クエリの部分  
  
 クエリで範囲変数の型は、データ ソース内の要素の型と互換性のあるする必要があります。 クエリ変数の型で定義されたシーケンスの要素と互換性のある必要があります、`Select`句。 最後に、シーケンスの要素の型もする必要がありますで使用されているループ コントロール変数の型と互換性のある、`For Each`クエリを実行するステートメント。 この厳密な型指定には、コンパイル時に型のエラーの識別が容易にします。  
  
 Visual Basic が容易厳密な型指定とも呼ばれるローカル型推論を実装することによって*暗黙の型指定*です。 機能は、前の例で使用して、全体で使用されることが表示されます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]のサンプルとドキュメントです。 Visual basic でローカル型推論を使用するだけで完了、`Dim`ステートメントなし、`As`句。 次の例では、`city`を文字列として厳密に型指定します。  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  ローカル型推論は場合にのみ機能`Option Infer`に設定されている`On`です。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)です。  
  
 ただし、クエリでローカル型推論を使用する場合でも同じ型の関係は、データ ソース内の変数、クエリ変数、およびクエリの実行ループの間に存在します。 作成しているときにこれらの型の関係の基本を理解すると便利ですが[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ、または作業用サンプルとドキュメントのコード例を使用します。  
  
 たとえば、データ ソースから返される型と一致しない範囲変数の明示的な型を指定する必要があります。 使用して、範囲変数の種類を指定することができます、`As`句。 その結果、エラーに変換すると、[縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と`Option Strict`に設定されている`On`です。 したがって、データ ソースから取得した値を変換を実行することをお勧めします。 使用して、明示的な範囲変数の型のデータ ソースからの値を変換することができます、<xref:System.Linq.Enumerable.Cast%2A>メソッドです。 選択した値をキャストすることも、`Select`句の範囲変数の型とは異なる、明示的な型にします。 これらのポイントは、次のコードに示します。  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>ソース データの全体の要素を返すクエリ  
 次の例は、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]操作、ソース データから選択した要素のシーケンスを返すクエリを実行します。 ソース`names`文字列の配列が含まれ、クエリの出力は M という文字で始まる文字列を含むシーケンス。  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 これは次のコードに相当はより短く、記述を簡単にです。 クエリでローカル型推論の依存は、Visual Basic で推奨されるスタイルです。  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 次のリレーションシップは、種類が暗黙的または明示的に決定されるかどうか、前のコード例の両方に存在します。  
  
1.  データ ソース内の要素の型`names`、範囲変数の型は、`name`クエリにします。  
  
2.  選択されているオブジェクトの種類`name`、クエリ変数の種類を決定`mNames`です。 ここで`name`は string では、そのため、クエリ変数は Visual Basic での IEnumerable (Of String)。  
  
3.  定義されたクエリ`mNames`で実行される、`For Each`ループします。 ループは、クエリの実行の結果を反復処理します。 `mNames`が実行されると、ループの反復変数、文字列のシーケンスを返す`nm`も文字列です。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>選択した要素から 1 つのフィールドを返すクエリ  
 次の例は、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]クエリ、データ ソースから選択した各要素の一部分のみを含むシーケンスを返す操作。 クエリのコレクションを受け取って`Customer`、データ ソースとしてオブジェクトおよびプロジェクトのみ、`Name`プロパティを結果にします。 顧客名は、文字列であるため、クエリは出力として文字列のシーケンスを作成します。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 変数間のリレーションシップは、単純な例のようです。  
  
1.  データ ソース内の要素の型`customers`、範囲変数の型は、`cust`クエリにします。 この例では型に対して`Customer`です。  
  
2.  `Select`ステートメントから返される、`Name`の各プロパティ`Customer`オブジェクト全体ではなくオブジェクト。 `Name`文字列で、クエリ変数`custNames`、もう一度されません (文字列) の IEnumerable の`Customer`します。  
  
3.  `custNames`文字列のシーケンスを表す、`For Each`ループの反復変数`custName`文字列である必要があります。  
  
 ローカル型推論、せず、前の例を記述し、次の例を理解するのには煩雑になります。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>匿名型を必要とするクエリ  
 次の例より複雑な状況を示しています。 前の例では、すべての変数の型を明示的に指定するときに便利でした。 この例ではことはできません。 全体を選択する代わりに`Customer`データ ソース、または各要素から 1 つのフィールドからの要素、`Select`このクエリ内の句は、元の 2 つのプロパティを返します`Customer`オブジェクト:`Name`と`City`です。 応答、`Select`句、コンパイラはこれら 2 つのプロパティを含む匿名型を定義します。 実行結果`nameCityQuery`で、`For Each`ループは、新しい匿名型のインスタンスのコレクション。 型を指定することはできません、匿名型に使用可能な名前があるないため`nameCityQuery`または`custInfo`明示的にします。 つまり、匿名型を含む名前があるない型の代わりに使用する`String`で`IEnumerable(Of String)`です。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 前の例ですべての変数の型を指定することはありませんが、リレーションシップが同じになります。  
  
1.  データ ソース内の要素の型が、クエリで範囲変数の型です。 この例では`cust`のインスタンスは、`Customer`です。  
  
2.  `Select`ステートメントは、匿名型をクエリ変数を生成する`nameCityQuery`、匿名型として暗黙的に型指定する必要があります。 匿名型は、使用可能な名前を持たず、したがって、明示的に指定することはできません。  
  
3.  反復変数の型、`For Each`ループは、手順 2. で作成された匿名型。 型に使用可能な名前があるないために、ループの反復変数の型は暗黙的に決定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [クエリ](../../../../visual-basic/language-reference/queries/queries.md)
