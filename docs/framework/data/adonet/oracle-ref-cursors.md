---
title: "Oracle REF CURSOR | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Oracle REF CURSOR
.NET Framework Data Provider for Oracle は、Oracle **REF CURSOR** データ型をサポートしています。  データ プロバイダーを使用して Oracle REF CURSOR を操作するときは、次の動作を考慮する必要があります。  
  
> [!NOTE]
>  動作の中には、Microsoft OLE DB Provider for Oracle \(MSDAORA\) の動作と異なるものがあります。  
  
-   パフォーマンスの理由から、Data Provider for Oracle では、バインドするよう明示的に指定した場合を除き、**REF CURSOR** データ型が自動的にバインドされることはありません。これは、MSDAORA の場合と同じです。  
  
-   データ プロバイダーでは、REF CURSOR パラメーターの指定に使用する {resultset} エスケープのような、ODBC エスケープ シーケンスはサポートされていません。  
  
-   REF CURSOR を返すストアド プロシージャを実行するには、**Cursor** の <xref:System.Data.OracleClient.OracleType>、および **Output** の <xref:System.Data.OracleClient.OracleParameter.Direction%2A> を使用して、<xref:System.Data.OracleClient.OracleParameterCollection> にパラメーターを定義する必要があります。  データ プロバイダーでは、REF CURSOR のバインドは出力パラメーターとしてのみサポートされています。  プロバイダーは、入力パラメーターとしての REF CURSOR はサポートしていません。  
  
-   パラメーター値からの <xref:System.Data.OracleClient.OracleDataReader> の取得はサポートされていません。  値は、コマンドを実行すると <xref:System.DBNull> 型になります。  
  
-   REF CURSOR を使用する **CommandBehavior** 列挙型値のみが **CloseConnection** になります \(たとえば、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> の呼び出し時\)。その他の値はすべて無視されます。  
  
-   **OracleDataReader** 内の REF CURSOR の順序は、**OracleParameterCollection** 内のパラメーターの順序で決まります。  <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> プロパティは無視されます。  
  
-   PL\/SQL の **TABLE** データ型はサポートされていません。  ただし、REF CURSOR は、さらに効果的です。  **TABLE** データ型を使用しなければならない場合、MSDAORA と共に OLE DB .NET データ プロバイダーを使用してください。  
  
## このセクションの内容  
 [REF CURSOR の例](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 次の 3 つの例を使って REF CURSOR の使い方について説明します。  
  
 [OracleDataReader の REF CURSOR パラメーター](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 REF CURSOR パラメーターを返し、**OracleDataReader** として値を読み取る、PL\/SQL ストアド プロシージャを実行する方法について説明します。  
  
 [OracleDataReader を使用した複数の REF CURSOR からのデータの取得](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 REF CURSOR パラメーターを返し、**OracleDataReader** を使用して値を読み取る、PL\/SQL ストアド プロシージャを実行する方法について説明します。  
  
 [1 つまたは複数の REF CURSOR を使用した DataSet の値の設定](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する、PL\/SQL ストアド プロシージャを実行する方法について説明します。  
  
## 参照  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)