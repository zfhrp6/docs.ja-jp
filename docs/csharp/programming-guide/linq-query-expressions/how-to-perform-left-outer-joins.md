---
redirect_url: /dotnet/articles/csharp/linq/perform-left-outer-joins
caps.handback.revision: 23
---
# 方法 : 左外部結合を実行する (C# プログラミング ガイド)
左外部結合は、2 番目のコレクションに相関関係を持つ要素があるかどうかに関係なく、最初のコレクションの各要素が返される結合です。  グループ化結合の結果 <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> のメソッドを呼び出すことで、左外部結合を実行するには [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] を使用できます。  
  
## 使用例  
 グループ結合の結果で <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> メソッドを使用して、左外部結合を実行する方法の例を次に示します。  
  
 2 つのコレクションの左外部結合を作成する最初の手順では、グループ結合を使用して内部結合を実行します   \(このプロセスの詳細については、「[方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)」を参照してください\)。この例では、`Person` オブジェクトのリストは `Person` のオブジェクトに基づいて `Pet` オブジェクトのリストに一致 `Pet.Owner`内部結合。  
  
 2 番目の手順では、右側のコレクションに一致する要素がない場合でも、最初 \(左側\) のコレクションの各要素を結果セットに含めます。  これを行うには、グループ結合から一致する要素の各シーケンスで <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> を呼び出します。  この例では、<xref:System.Linq.Enumerable.DefaultIfEmpty%2A> は `Pet` のオブジェクトの一致の各シーケンスで呼び出されます。  メソッドは `Pet` のオブジェクトのシーケンスが `Person` のすべてのオブジェクトに対して空の場合、一つを含むコレクション、`Person` の各オブジェクトが結果のコレクションに表示されるように既定値を返します。  
  
> [!NOTE]
>  参照型の既定値はです `null`; したがって、この例では null 参照を持つように `Pet` の各コレクションの各要素にアクセスする前に確認します。  
  
 [!code-cs[CsLINQProgJoining#7](../../../csharp/programming-guide/linq-query-expressions/codesnippet/csharp/Joins/joins.cs#7)]  
  
## コードのコンパイル  
  
-   [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] で新しいコンソール アプリケーション プロジェクトを作成します。  
  
-   System.Core.dll がまだ参照されていない場合は、System.Core.dll への参照を追加します。  
  
-   <xref:System.Linq> 名前空間を含めます。  
  
-   `Program` クラスの `Main` のメソッドの下に program.cs ファイルに例からコードをコピーして貼り付けます。  `LeftOuterJoinExample` のメソッドを呼び出すに `Main` のメソッドのコード行を追加します。  
  
-   プログラムを実行します。  
  
## 参照  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [方法 : 内部結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-inner-joins.md)   
 [方法 : グループ化結合を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-grouped-joins.md)   
 [匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)