---
title: データベースからの単一の値の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
ms.openlocfilehash: b7ad989dce39a8e9a0ed7b6cd988e06304e7b40f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="1b537-102">データベースからの単一の値の取得</span><span class="sxs-lookup"><span data-stu-id="1b537-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="1b537-103">テーブルやデータ ストリームの形式ではなく、単に 1 つの値をデータベース情報として返すことが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1b537-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="1b537-104">たとえば、数などの集計関数の結果を返すにする可能性があります (\*)、SUM(Price)、または AVG(Quantity) です。</span><span class="sxs-lookup"><span data-stu-id="1b537-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="1b537-105">**コマンド**オブジェクトを使用して単一の値を返す機能を提供する、 **ExecuteScalar**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1b537-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="1b537-106">**ExecuteScalar**メソッドはスカラー値、結果セットの最初の行の最初の列の値として返します。</span><span class="sxs-lookup"><span data-stu-id="1b537-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="1b537-107"><xref:System.Data.SqlClient.SqlCommand> を使用して新しい値をデータベースに挿入するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b537-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="1b537-108">挿入したレコードの ID 列の値を取得するために、<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> メソッドが使用されています。</span><span class="sxs-lookup"><span data-stu-id="1b537-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1b537-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b537-109">See Also</span></span>  
 [<span data-ttu-id="1b537-110">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="1b537-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="1b537-111">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="1b537-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="1b537-112">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="1b537-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="1b537-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="1b537-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
