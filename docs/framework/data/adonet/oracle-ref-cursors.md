---
title: Oracle REF CURSOR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 277e12e59ea85be4d22e28a59bd7404e5e0111f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-ref-cursors"></a>Oracle REF CURSOR
.NET Framework Data Provider for Oracle には、Oracle がサポートしている**REF CURSOR**データ型。 データ プロバイダーを使用して Oracle REF CURSOR を操作するときは、次の動作を考慮する必要があります。  
  
> [!NOTE]
>  動作の中には、Microsoft OLE DB Provider for Oracle (MSDAORA) の動作と異なるものがあります。  
  
-   パフォーマンス上の理由から、Data Provider for Oracle に自動的にはバインドしません**REF CURSOR**データ型を MSDAORA と、明示的に指定する場合を除き、します。  
  
-   データ プロバイダーでは、REF CURSOR パラメーターの指定に使用する {resultset} エスケープのような、ODBC エスケープ シーケンスはサポートされていません。  
  
-   REF Cursor を返すストアド プロシージャを実行するには、内のパラメーターを定義する必要があります、<xref:System.Data.OracleClient.OracleParameterCollection>で、<xref:System.Data.OracleClient.OracleType>の**カーソル**と<xref:System.Data.OracleClient.OracleParameter.Direction%2A>の**出力**です。 データ プロバイダーでは、REF CURSOR のバインドは出力パラメーターとしてのみサポートされています。 プロバイダーは、入力パラメーターとしての REF CURSOR はサポートしていません。  
  
-   パラメーター値からの <xref:System.Data.OracleClient.OracleDataReader> の取得はサポートされていません。 値は、コマンドを実行すると <xref:System.DBNull> 型になります。  
  
-   唯一**CommandBehavior** REF Cursor で動作する列挙値 (を呼び出すときに、 <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) は**CloseConnection**; 他のすべてのユーザーは無視されます。  
  
-   内の REF Cursor の順序、 **OracleDataReader**では、パラメーターの順序によって異なります、 **OracleParameterCollection**です。 <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> プロパティは無視されます。  
  
-   PL/SQL**テーブル**データ型はサポートされていません。 ただし、REF CURSOR は、さらに効果的です。 使用する場合、**テーブル**MSDAORA で OLE DB .NET データ プロバイダーを使用して、データ型します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [REF CURSOR の例](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 次の 3 つの例を使って REF CURSOR の使い方について説明します。  
  
 [OracleDataReader の REF CURSOR パラメーター](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 返し、REF CURSOR パラメーターとして値を読み取る、PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**です。  
  
 [OracleDataReader を使用した複数の REF Cursor からのデータの取得](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 2 つの REF CURSOR パラメーターを返しを使用して値を読み取る PL/SQL ストアド プロシージャを実行する方法を示します、 **OracleDataReader**です。  
  
 [データセットを使用して 1 つまたは複数の REF Cursor](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する、PL/SQL ストアド プロシージャを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Oracle および ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
