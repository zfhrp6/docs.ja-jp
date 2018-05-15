---
title: '方法: CopyToDataTable を実装する&lt;T&gt;ジェネリック型 T が DataRow ではありません'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b27b52cf-6172-485f-a75c-70ff9c5a2bd4
ms.openlocfilehash: 77adcd1f2070ba3ccfe036d37384a7a855ebf132
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-implement-copytodatatablelttgt-where-the-generic-type-t-is-not-a-datarow"></a><span data-ttu-id="88290-102">方法: CopyToDataTable を実装する&lt;T&gt;ジェネリック型 T が DataRow ではありません</span><span class="sxs-lookup"><span data-stu-id="88290-102">How to: Implement CopyToDataTable&lt;T&gt; Where the Generic Type T Is Not a DataRow</span></span>
<span data-ttu-id="88290-103">データ バインドには、しばしば <xref:System.Data.DataTable> オブジェクトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="88290-103">The <xref:System.Data.DataTable> object is often used for data binding.</span></span> <span data-ttu-id="88290-104"><xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、クエリの結果を受け取り、そのデータを <xref:System.Data.DataTable> にコピーします。これをデータ バインドに利用できます。</span><span class="sxs-lookup"><span data-stu-id="88290-104">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> method takes the results of a query and copies the data into a <xref:System.Data.DataTable>, which can then be used for data binding.</span></span> <span data-ttu-id="88290-105">ただし、<xref:System.Data.DataTableExtensions.CopyToDataTable%2A> メソッドは、ジェネリック パラメーター <xref:System.Collections.Generic.IEnumerable%601> が `T` 型である <xref:System.Data.DataRow> ソースに対してのみ作用します。</span><span class="sxs-lookup"><span data-stu-id="88290-105">The <xref:System.Data.DataTableExtensions.CopyToDataTable%2A> methods, however, only operate on an <xref:System.Collections.Generic.IEnumerable%601> source where the generic parameter `T` is of type <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="88290-106">有用ではありますが、一連のスカラー型、匿名型を射影するクエリ、またはテーブルの結合を実行するクエリからは、テーブルを作成できません。</span><span class="sxs-lookup"><span data-stu-id="88290-106">Although this is useful, it does not allow tables to be created from a sequence of scalar types, from queries that project anonymous types, or from queries that perform table joins.</span></span>  
  
 <span data-ttu-id="88290-107">このトピックでは、`CopyToDataTable<T>` 型以外のジェネリック パラメーター `T` を受け取る 2 つのカスタム <xref:System.Data.DataRow> 拡張メソッドを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88290-107">This topic describes how to implement two custom `CopyToDataTable<T>` extension methods that accept a generic parameter `T` of a type other than <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="88290-108"><xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成するロジックは、`ObjectShredder<T>` クラスに存在し、オーバーロードされた 2 つの `CopyToDataTable<T>` 拡張メソッドにラップされています。</span><span class="sxs-lookup"><span data-stu-id="88290-108">The logic to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source is contained in the `ObjectShredder<T>` class, which is then wrapped in two overloaded `CopyToDataTable<T>` extension methods.</span></span> <span data-ttu-id="88290-109">`Shred` クラスの `ObjectShredder<T>` メソッドは、データが格納された <xref:System.Data.DataTable> を返し、<xref:System.Collections.Generic.IEnumerable%601> ソース、<xref:System.Data.DataTable>、および <xref:System.Data.LoadOption> 列挙型の 3 つの入力パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="88290-109">The `Shred` method of the `ObjectShredder<T>` class returns the filled <xref:System.Data.DataTable> and accepts three input parameters: an <xref:System.Collections.Generic.IEnumerable%601> source, a <xref:System.Data.DataTable>, and a <xref:System.Data.LoadOption> enumeration.</span></span> <span data-ttu-id="88290-110">返される <xref:System.Data.DataTable> の最初のスキーマは、`T` 型のスキーマに基づきます。</span><span class="sxs-lookup"><span data-stu-id="88290-110">The initial schema of the returned <xref:System.Data.DataTable> is based on the schema of the type `T`.</span></span> <span data-ttu-id="88290-111">既存のテーブルを入力として指定する場合は、そのスキーマが、`T` 型のスキーマと矛盾がないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="88290-111">If an existing table is provided as input, the schema must be consistent with the schema of the type `T`.</span></span> <span data-ttu-id="88290-112">返されたテーブルでは、`T` 型のパブリック プロパティおよびパブリック フィールドが、それぞれ <xref:System.Data.DataColumn> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="88290-112">Each public property and field of the type `T` is converted to a <xref:System.Data.DataColumn> in the returned table.</span></span> <span data-ttu-id="88290-113">`T` から派生した型がソース シーケンスに含まれている場合は、返されるテーブルのスキーマが、あらゆる追加パブリック プロパティまたは追加パブリック フィールドに展開されます。</span><span class="sxs-lookup"><span data-stu-id="88290-113">If the source sequence contains a type derived from `T`, the returned table schema is expanded for any additional public properties or fields.</span></span>  
  
 <span data-ttu-id="88290-114">例については、ユーザー設定を使用する`CopyToDataTable<T>`メソッドを参照してください[、クエリからデータ テーブルを作成する](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)です。</span><span class="sxs-lookup"><span data-stu-id="88290-114">For examples of using the custom `CopyToDataTable<T>` methods, see [Creating a DataTable From a Query](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md).</span></span>  
  
### <a name="to-implement-the-custom-copytodatatablet-methods-in-your-application"></a><span data-ttu-id="88290-115">カスタム CopyToDataTable を実装する\<T >、アプリケーション内のメソッド</span><span class="sxs-lookup"><span data-stu-id="88290-115">To implement the custom CopyToDataTable\<T> methods in your application</span></span>  
  
1.  <span data-ttu-id="88290-116">`ObjectShredder<T>` クラスを実装して、<xref:System.Data.DataTable> ソースから <xref:System.Collections.Generic.IEnumerable%601> を作成します。</span><span class="sxs-lookup"><span data-stu-id="88290-116">Implement the `ObjectShredder<T>` class to create a <xref:System.Data.DataTable> from an <xref:System.Collections.Generic.IEnumerable%601> source:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#objectshredderclass)]
     [!code-vb[DP Custom CopyToDataTable Examples#ObjectShredderClass](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#objectshredderclass)]  
  
2.  <span data-ttu-id="88290-117">カスタム `CopyToDataTable<T>` 拡張メソッドをクラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="88290-117">Implement the custom `CopyToDataTable<T>` extension methods in a class:</span></span>  
  
     [!code-csharp[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/CS/Program.cs#customcopytodatatablemethods)]
     [!code-vb[DP Custom CopyToDataTable Examples#CustomCopyToDataTableMethods](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP Custom CopyToDataTable Examples/VB/Module1.vb#customcopytodatatablemethods)]  
  
3.  <span data-ttu-id="88290-118">`ObjectShredder<T>` クラスおよび `CopyToDataTable<T>` 拡張メソッドをアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="88290-118">Add the `ObjectShredder<T>` class and `CopyToDataTable<T>` extension methods to your application.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        ' Your application code using CopyToDataTable<T>.  
    End Sub  
End Module  
  
Public Module CustomLINQtoDataSetMethods  
…  
End Module  
  
Public Class ObjectShredder(Of T)  
…  
End Class
```
  
```csharp
class Program  
{  
    static void Main(string[] args)  
    {  
        // Your application code using CopyToDataTable<T>.  
    }  
}  
public static class CustomLINQtoDataSetMethods  
{  
…  
}  
public class ObjectShredder<T>  
{  
…  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="88290-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="88290-119">See Also</span></span>  
 [<span data-ttu-id="88290-120">クエリによる DataTable の作成</span><span class="sxs-lookup"><span data-stu-id="88290-120">Creating a DataTable From a Query</span></span>](../../../../docs/framework/data/adonet/creating-a-datatable-from-a-query-linq-to-dataset.md)  
 [<span data-ttu-id="88290-121">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="88290-121">Programming Guide</span></span>](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
