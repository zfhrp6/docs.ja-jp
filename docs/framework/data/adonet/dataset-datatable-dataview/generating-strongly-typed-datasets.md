---
title: 厳密に型指定された DataSet の生成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 95bb536416a043fc392d0c4e94378239ae3ee37f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="generating-strongly-typed-datasets"></a>厳密に型指定された DataSet の生成
XML スキーマ定義言語 (XSD) 標準に準拠する XML スキーマがあれば、<xref:System.Data.DataSet> に付属の XSD.exe ツールを使用して、厳密に型指定された [!INCLUDE[winsdklong](../../../../../includes/winsdklong-md.md)] を生成できます。  
  
 (データベース テーブルから xsd を作成するを参照してください。<xref:System.Data.DataSet.WriteXmlSchema%2A>または[Visual Studio でのデータセットの操作](http://msdn.microsoft.com/library/8bw9ksd6.aspx))。  
  
 次のコードを生成するための構文を示しています、**データセット**このツールを使用します。  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 この構文では、`/d`ディレクティブを生成するツールに指示、**データセット**、および`/l:`(たとえば、c# または Visual Basic .NET など) を使用する言語をどのようなツールに指示します。 省略可能な`/eld`ディレクティブは、使用できることを指定します[!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]生成をクエリする**データセット。** このオプションは、`/d` オプションと組み合わせて指定します。 詳細については、次を参照してください。[型指定されたデータセットのクエリを実行する](../../../../../docs/framework/data/adonet/querying-typed-datasets.md)です。 省略可能な`/n:`ディレクティブは名前空間を生成するツール、**データセット**と呼ばれる**XSDSchema.Namespace**です。 コマンドの出力は XSDSchemaFileName.cs で、ADO.NET アプリケーションでコンパイルおよび使用できます。 生成されたコードをライブラリまたはモジュールとしてコンパイルできます。  
  
 C# コンパイラ (csc.exe) を使用して、生成されたコードをライブラリとしてコンパイルする構文を次のコードで示します。  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` ディレクティブはライブラリとしてコンパイルすることをツールに知らせ、`/r:` ディレクティブはコンパイルに必要な依存ライブラリを指定します。 コマンドの出力は XSDSchemaFileName.dll で、`/r:` ディレクティブによる ADO.NET アプリケーションのコンパイル時にコンパイラに渡すことができます。  
  
 ADO.NET アプリケーションの XSD.exe に渡された名前空間にアクセスする構文を次のコードで示します。  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 次のコード例は、型指定された**データセット**という**CustomerDataSet**在住の顧客の一覧を読み込む、 **Northwind**データベース。 使用して、データが読み込まれた後、**塗りつぶし**メソッドの例は、各顧客をループ処理、**顧客**表に、型指定されたを使用して**CustomersRow** (**DataRow**) オブジェクト。 これによりに直接アクセスする、 **CustomerID**列を経由せず、 **DataColumnCollection**です。  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 例に使用された XML スキーマを次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataSet>  
 [型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
