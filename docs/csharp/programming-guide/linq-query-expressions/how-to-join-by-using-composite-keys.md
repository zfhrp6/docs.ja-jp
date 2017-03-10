---
redirect_url: /dotnet/articles/csharp/linq/join-by-using-composite-keys
caps.handback.revision: 8
---
# 方法 : 複合キーを使用して結合する (C# プログラミング ガイド)
この例では、複数のキーを使用して一致を定義する結合操作の実行方法を示します。  この操作を行うためには、複合キーを使用します。  複合キーは、比較する値を指定した匿名型または名前付きの型として作成します。  クエリ変数がメソッド境界を越えて渡される場合は、キーの <xref:System.Object.Equals%2A> と <xref:System.Object.GetHashCode%2A> をオーバーライドする名前付きの型を使用します。  プロパティの名前とその出現順序は、各キーで同じでなければなりません。  
  
## 使用例  
 次の例は、複合キーを使用して 3 つのテーブルのデータを結合する方法を示しています。  
  
```  
var query = from o in db.Orders  
    from p in db.Products  
    join d in db.OrderDetails   
        on new {o.OrderID, p.ProductID} equals new {d.OrderID,         d.ProductID} into details  
        from d in details  
        select new {o.OrderID, p.ProductID, d.UnitPrice};  
```  
  
 複合キーに対する型の推定は、キーに含まれるプロパティの名前と、その出現順序によって決まります。  ソース シーケンス内のプロパティの名前が同じでない場合は、キーで新しい名前を割り当てる必要があります。  たとえば、`Orders` テーブルと `OrderDetails` テーブルの列にそれぞれ異なる名前が使用されている場合は、次のように同一の名前を割り当てることによって匿名型の複合キーを作成できます。  
  
```  
join...on new {Name = o.CustomerName, ID = o.CustID} equals   
    new {Name = d.CustName, ID = d.CustID }  
```  
  
 複合キーは、`group` 句でも使用できます。  
  
## コードのコンパイル  
  
-   このコードをコンパイルおよび実行するには、次の手順で行います。  
  
-   「[方法: Northwind データベースへの接続](../Topic/How%20to:%20Connect%20to%20the%20Northwind%20Database.md)」を開き、指示に従ってプロジェクトをセットアップし、データベース接続を作成します。  詳細については、「[方法 : サンプル データベースをインストールする](../Topic/How%20to:%20Install%20Sample%20Databases.md)」を参照してください。  
  
-   samples.cs で、db という Northwind 入力パラメーターを受け取る新しい空のメソッドを作成します \(このファイル内の他のメソッドと同様\)。  この例のコードを、メソッド本体に貼り付けます。  
  
-   program.cs を、`Main` から新しいメソッドを呼び出すように変更します。  
  
-   F5 キーを押してクエリをコンパイルおよび実行します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [join 句](../../../csharp/language-reference/keywords/join-clause.md)   
 [group 句](../../../csharp/language-reference/keywords/group-clause.md)