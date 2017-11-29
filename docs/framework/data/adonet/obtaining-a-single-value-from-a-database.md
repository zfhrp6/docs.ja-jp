---
title: "データベースからの単一の値の取得"
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
ms.assetid: b38526cd-a62a-48cb-822a-e91dfa68e02d
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 513310ddfb578f127ee70059dec386f207180907
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-a-single-value-from-a-database"></a><span data-ttu-id="56328-102">データベースからの単一の値の取得</span><span class="sxs-lookup"><span data-stu-id="56328-102">Obtaining a Single Value from a Database</span></span>
<span data-ttu-id="56328-103">テーブルやデータ ストリームの形式ではなく、単に 1 つの値をデータベース情報として返すことが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="56328-103">You may need to return database information that is simply a single value rather than in the form of a table or data stream.</span></span> <span data-ttu-id="56328-104">たとえば、数などの集計関数の結果を返すにする可能性があります (\*)、SUM(Price)、または AVG(Quantity) です。</span><span class="sxs-lookup"><span data-stu-id="56328-104">For example, you may want to return the result of an aggregate function such as COUNT(\*), SUM(Price), or AVG(Quantity).</span></span> <span data-ttu-id="56328-105">**コマンド**オブジェクトを使用して単一の値を返す機能を提供する、 **ExecuteScalar**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="56328-105">The **Command** object provides the capability to return single values using the **ExecuteScalar** method.</span></span> <span data-ttu-id="56328-106">**ExecuteScalar**メソッドはスカラー値、結果セットの最初の行の最初の列の値として返します。</span><span class="sxs-lookup"><span data-stu-id="56328-106">The **ExecuteScalar** method returns, as a scalar value, the value of the first column of the first row of the result set.</span></span>  
  
 <span data-ttu-id="56328-107"><xref:System.Data.SqlClient.SqlCommand> を使用して新しい値をデータベースに挿入するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="56328-107">The following code example inserts a new value in the database using a <xref:System.Data.SqlClient.SqlCommand>.</span></span> <span data-ttu-id="56328-108">挿入したレコードの ID 列の値を取得するために、<xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> メソッドが使用されています。</span><span class="sxs-lookup"><span data-stu-id="56328-108">The <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A> method is used to return the identity column value for the inserted record.</span></span>  
  
 [!code-csharp[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/CS/source.cs#1)]
 [!code-vb[DataWorks SqlCommand.ExecuteScalar#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlCommand.ExecuteScalar/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="56328-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="56328-109">See Also</span></span>  
 [<span data-ttu-id="56328-110">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="56328-110">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="56328-111">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="56328-111">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="56328-112">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="56328-112">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="56328-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="56328-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
