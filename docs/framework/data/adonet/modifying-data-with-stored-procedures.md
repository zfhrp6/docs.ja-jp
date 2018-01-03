---
title: "ストアド プロシージャでのデータの変更"
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
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5df938d6d55786c12e6d73171d2a5cb33f80ea84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-data-with-stored-procedures"></a>ストアド プロシージャでのデータの変更
ストアド プロシージャは、入力パラメーターとしてデータを受け取り、出力パラメーター、結果セット、または戻り値としてデータを返すことができます。 以下のサンプルでは、入力パラメーター、出力パラメーター、および戻り値が ADO.NET によってどのようにやり取りされるかを示したものです。 この例では、主キー列が SQL Server データベースの ID 列であるテーブルに新しいレコードを挿入しています。  
  
> [!NOTE]
>  SQL Server のストアド プロシージャで、<xref:System.Data.SqlClient.SqlDataAdapter> を使用してデータを編集または削除する場合、ストアド プロシージャの定義に SET NOCOUNT ON は使用しないでください。 処理された行数がゼロとして返され、`DataAdapter` によって同時実行の競合として解釈されてしまいます。 この場合、<xref:System.Data.DBConcurrencyException> がスローされます。  
  
## <a name="example"></a>例  
 このサンプルでは、次のストアド プロシージャを使用してに新しいカテゴリを挿入、 **Northwind** **カテゴリ**テーブル。 ストアド プロシージャ値を受け取り、 **CategoryName** 、SCOPE_IDENTITY() を使用して、入力パラメーターとして列が id フィールドの新しい値を取得する関数**CategoryID**、返す出力パラメーターです。 RETURN ステートメントを使用して、@@ROWCOUNT挿入された行の数を返す関数。  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 上述の `InsertCategory` ストアド プロシージャを <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> の <xref:System.Data.SqlClient.SqlDataAdapter> のソースとして使用する例を次に示します。 `@Identity` 出力パラメーターは、<xref:System.Data.DataSet> の `Update` メソッドが呼び出され、データベースにレコードが挿入された後で <xref:System.Data.SqlClient.SqlDataAdapter> に反映されます。 戻り値も取得されます。  
  
> [!NOTE]
>  使用する場合、<xref:System.Data.OleDb.OleDbDataAdapter>を持つパラメーターを指定する必要があります、<xref:System.Data.ParameterDirection>の**ReturnValue**他のパラメーターの前にします。  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [コマンドの実行](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
