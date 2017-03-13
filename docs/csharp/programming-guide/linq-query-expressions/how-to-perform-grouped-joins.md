---
redirect_url: /dotnet/articles/csharp/linq/perform-grouped-joins
caps.handback.revision: 23
---
# 方法 : グループ化結合を実行する (C# プログラミング ガイド)
グループ化結合は、階層データ構造を作成する場合に便利です。  グループ化結合は、最初のコレクションの各要素と、2 番目のコレクションの相関関係を持つ要素のセットを組み合わせたものです。  
  
 たとえば、Student という名前のクラスまたはリレーショナル データベース テーブルに、Id と Name の 2 つのフィールドがあるとします。  また、Course という名前の 2 番目のクラスまたはリレーショナル データベース テーブルに、StudentId と CourseTitle の 2 つのフィールドがあるとします。  一致する Student.Id と Course.StudentId に基づいて、これらのデータ ソースのグループ化結合を行うと、Course オブジェクトのコレクションを持つ各 Student がグループ化されます \(コレクションは空の場合もあります\)。  
  
> [!NOTE]
>  最初のコレクションの各要素は、2 番目のコレクションに相関関係を持つ要素があるかどうかに関係なく、グループ化結合の結果セットに表示されます。  相関関係を持つ要素が見つからない場合、その要素の相関関係を持つ要素のシーケンスは空になります。  したがって、結果セレクターは最初のコレクションのすべての要素にアクセスできます。  これは、非グループ化結合の結果セレクターとは異なります。非グループ化結合の結果セレクターは、2 番目のコレクションに一致するものがない最初のコレクションの要素にアクセスすることはできません。  
  
 このトピックの最初の例では、グループ化結合を実行する方法を示します。  2 番目の例では、グループ化結合を使用して XML 要素を作成する方法を示します。  
  
## 使用例  
  
### グループ化結合の例  
 `Pet.Owner` プロパティと一致する `Person` に基づいて、`Person` オブジェクトと `Pet` オブジェクトの型のグループ化結合を行う例を次に示します。  一致ごとにペアを作成する非グループ化結合と異なり、グループ化結合では、最初のコレクションの要素ごとに 1 つのオブジェクト \(この例では `Person` オブジェクト\) のみを作成します。  次に、2 番目のコレクションの対応する要素 \(この例では `Pet` オブジェクト\) がコレクションにグループ化されます。  最後に、結果セレクター機能により、`Person.FirstName` と `Pet` オブジェクトのコレクションで構成される一致ごとに匿名型が作成されます。  
  
 [!code-cs[CsLINQProgJoining#5](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_1.cs)]  
  
## 使用例  
  
### XML を作成するグループ化結合の例  
 グループ化結合は、[!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] を使用して XML を作成するのに適しています。  次の例は前の例に似ていますが、匿名型を作成するのではなく、結果セレクター機能により、結合されたオブジェクトを表す XML 要素を作成する点が異なります。  [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] の詳細については、「[LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)」を参照してください。  
  
 [!code-cs[CsLINQProgJoining#6](../../../csharp/programming-guide/linq-query-expressions/codesnippet/CSharp/how-to-perform-grouped-joins_2.cs)]  
  
## コードのコンパイル  
  
-   [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] で新しい**コンソール アプリケーション** プロジェクトを作成します。  
  
-   System.Core.dll と System.Xml.Linq.dll がまだ参照されていない場合は、System.Core.dll と System.Xml.Linq.dll への参照を追加します。  
  
-   <xref:System.Linq> 名前空間と <xref:System.Xml.Linq> 名前空間を含めます。  
  
-   例からコードをコピーし、program.cs ファイルの `Main` メソッドの下に貼り付けます。  貼り付けたメソッドを呼び出すコード行を `Main` メソッドに追加します。  
  
-   プログラムを実行します。  
  
## 参照  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [方法 : 左外部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-left-outer-joins.md)   
 [LINQ to XML](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)