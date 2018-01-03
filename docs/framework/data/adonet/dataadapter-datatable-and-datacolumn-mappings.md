---
title: "DataAdapter DataTable と DataColumn のマップ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3df07f8b7bf71d658e9073a8aeb3d51dee087544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable と DataColumn のマップ
A **DataAdapter** 0 個以上のコレクションを含んでいます<xref:System.Data.Common.DataTableMapping>内のオブジェクトの**TableMappings**プロパティです。 A **DataTableMapping** 、データ ソースに対するクエリから返されるデータの間のマスター マッピングを提供し、<xref:System.Data.DataTable>です。 **DataTableMapping**の代わりに名前を渡すことができます、 **DataTable**名、**塗りつぶし**のメソッド、 **DataAdapter**です。 次の例を作成、 **DataTableMapping**という**AuthorsMapping**の**作成者**テーブル。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping**内の列名を使用することができます、 **DataTable**は異なるデータベースにします。 **DataAdapter**マッピングを使用して、テーブルが更新されたときに、列を照合します。  
  
 指定しない場合、 **TableName**または**DataTableMapping**名前を呼び出すときに、**塗りつぶし**または**更新**のメソッド、 **DataAdapter**、 **DataAdapter**は検索、 **DataTableMapping** "Table"という名前です。 場合は、その**DataTableMapping**が存在しない、 **TableName**の**DataTable** 「テーブル」です。 既定値を指定することができます**DataTableMapping**作成することで、 **DataTableMapping** "Table"の名前に置き換えます。  
  
 次のコード例を作成、 **DataTableMapping** (から、<xref:System.Data.Common>名前空間) を指定された既定のマッピングを返し**DataAdapter** "Table"名前を付けることによってです。 例では、クエリ結果内の最初のテーブルから列をマップし、(、**顧客**のテーブル、 **Northwind**データベース) にわかりやすい名前のセットを**Northwind の Customers**テーブルに、<xref:System.Data.DataSet>です。 割り当てられない列には、データ ソースの列名が使用されます。  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 高度な状況は、同じするを決めることがあります**DataAdapter**異なるマッピングに別のテーブルの読み込みをサポートするためにします。 これを行うには、単に追加**DataTableMapping**オブジェクト。  
  
 ときに、**塗りつぶし**メソッドのインスタンスに渡されます、**データセット**と**DataTableMapping** 、その名前のマッピングが存在する場合、名前が使用されますそれ以外の場合、、  **。DataTable**名を使用するとします。  
  
 次の例では、作成、 **DataTableMapping**の名前を持つ**顧客**と**DataTable**の名前**BizTalkSchema**です。 例では、SELECT ステートメントによって返される行にマップされます、 **BizTalkSchema** **DataTable**です。  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。 列マッピングがの増分の既定の名前を指定した場合は、列マッピングの基になる列が指定されていません、 **SourceColumn** *N、*で始まる**SourceColumn1**です。 テーブル マップにソース テーブル名を指定しない場合、テーブルのマッピングが指定されたのインクリメンタル既定名**SourceTable** *N*以降で、 **SourceTable1**です。  
  
> [!NOTE]
>  名前付け規則を回避することをお勧め**SourceColumn** *N*列マッピングの場合、または**SourceTable** *N*テーブル指定した名前の既存の既定の列マップ名の競合する場合もあるため、マッピング、 **ColumnMappingCollection**またはテーブル マップ名に、 **DataTableMappingCollection**. 指定した名前が既に存在する場合は、例外がスローされます。  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 場合、 **SelectCommand**複数のテーブルを返します**塗りつぶし**内のテーブルの増分値を持つテーブル名を自動的に生成、**データセット**以降で、形式でテーブル名と続行を指定**TableName** *N*以降で、 **TableName1**です。 内のテーブルに対して指定名前に、自動的に生成されたテーブル名をマップするテーブルのマッピングを使用することができます、**データセット**です。 たとえば、 **SelectCommand** 2 つのテーブルを返す**顧客**と**Orders**、次の呼び出しを発行**塗りつぶし**です。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 2 つのテーブルに作成されます、**データセット**:**顧客**と**Customers1**です。 テーブルのマッピングを使用するには 2 番目のテーブルがという名前のことを確認する**Orders**の代わりに**Customers1**です。 これを行うには、マップのソース テーブル**Customers1**を**データセット**テーブル**注文**の次の例に示すようにします。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>参照  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
