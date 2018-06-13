---
title: DataTable の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: a374c7c6e7dfc04cd8828208d6762f8d8665072e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767168"
---
# <a name="creating-a-datatable"></a>DataTable の作成
<xref:System.Data.DataTable> は 1 つのインメモリ リレーショナル データのテーブルを表します。DataTable は単独で作成および使用することも、他の .NET Framework オブジェクトから <xref:System.Data.DataSet> のメンバーとして使用することもできます。  
  
 作成することができます、 **DataTable** 、適切なを使用してオブジェクト**DataTable**コンス トラクターです。 追加することができます、**データセット**を使用して、**追加**に追加する方法、 **DataTable**オブジェクトの**テーブル**コレクション。  
  
 作成することも**DataTable**内のオブジェクトは、**データセット**を使用して、**塗りつぶし**または**FillSchema**のメソッド、 **DataAdapter**オブジェクト、または、定義済みまたは推論されたスキーマを使用して XML から、 **ReadXml**、 **ReadXmlSchema**、または**InferXmlSchema**メソッド、**データセット**です。 追加した後に注意してください、 **DataTable**のメンバーとして、**テーブル**いずれかのコレクション**データセット**、他の任意ののテーブルのコレクションに追加することはできません**データセット**です。  
  
 作成する場合、 **DataTable**スキーマ (つまり、構造体) はありません。 テーブルのスキーマを定義するのには必要がありますを作成し、追加<xref:System.Data.DataColumn>オブジェクトを**列**テーブルのコレクション。 テーブルの主キー列を定義し、作成して追加**制約**オブジェクトを**制約**テーブルのコレクション。 スキーマを定義した後、 **DataTable**、行のデータをテーブルに追加するには追加することによって**DataRow**オブジェクトを**行**テーブルのコレクション。  
  
 値を指定する必要はありません、<xref:System.Data.DataTable.TableName%2A>プロパティを作成するとき、 **DataTable**; プロパティを指定するには、いつでもまたはすることが空白のままにします。 ただし、せず、テーブルを追加する、 **TableName**値を**データセット**、テーブルがテーブルの増分の既定の名前を指定する*N*、table0"Table"で開始します。  
  
> [!NOTE]
>  避けることをお勧め、"テーブル*N*"名前付け規則を指定するときに、 **TableName**値、指定した名前の既存の既定のテーブル名と競合する場合もあるため、**データセット**. 指定した名前が既に存在する場合は、例外がスローされます。  
  
 次の例のインスタンスを作成する、 **DataTable**オブジェクトし、"Customers"という名前を割り当てる  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 次の例のインスタンスを作成する、 **DataTable**に追加することによって、**テーブル**のコレクション、**データセット**です。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [DataAdapter からの DataSet の読み込み](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
