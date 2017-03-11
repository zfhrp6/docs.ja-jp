---
redirect_url: /dotnet/articles/csharp/linq/create-a-nested-group
caps.handback.revision: 12
---
# 方法: 入れ子になったグループを作成する (C# プログラミング ガイド)
[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] クエリ式で入れ子になったグループを作成する方法を次の例に示します。  学年または成績レベルに基づいて作成した各グループを、さらに各自の名前に基づくグループに分割します。  
  
## 使用例  
 [!code-cs[csProgGuideLINQ#24](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#24)]  
  
 入れ子になったグループの内部の要素を反復処理するために、3 つの入れ子になった `foreach` ループが必要です。  
  
## コードのコンパイル  
 この例には、「[方法 : オブジェクトのコレクションを照会する](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)」のサンプル アプリケーションで定義されているオブジェクトへの参照があります。  このメソッドをコンパイルして実行するには、メソッドをそのアプリケーションの `StudentClass` クラスに貼り付け、`Main` メソッドからそのメソッドを呼び出すコードを追加します。  
  
 独自のアプリケーションに合わせてこのメソッドを変更する場合、LINQ には [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 が必要なこと、および System.Core.dll への参照と System.Linq の using ディレクティブをプロジェクトに含める必要があることに注意してください。  LINQ to SQL、LINQ to XML、および LINQ to DataSet の場合は、追加の using と参照も必要です。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)