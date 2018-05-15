---
title: DbProviderFactories
ms.date: 03/30/2017
ms.assetid: 2a8e2640-3a49-42a1-a3a9-b43026907ae1
ms.openlocfilehash: 8692dc761f00e0ddc8ec9fad5a5df66b7fda7916
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dbproviderfactories"></a><span data-ttu-id="a1d90-102">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a1d90-102">DbProviderFactories</span></span>
<span data-ttu-id="a1d90-103"><xref:System.Data.Common> 名前空間には、特定のデータ ソースを使用するための <xref:System.Data.Common.DbProviderFactory> インスタンスを作成するクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a1d90-103">The <xref:System.Data.Common> namespace provides classes for creating <xref:System.Data.Common.DbProviderFactory> instances to work with specific data sources.</span></span> <span data-ttu-id="a1d90-104"><xref:System.Data.Common.DbProviderFactory> インスタンスを作成し、データ プロバイダーに関する情報をそのインスタンスに渡すと、`DbProviderFactory` はあらかじめ提供された情報に基づいて厳密に型指定された正しいオブジェクトを判断して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a1d90-104">When you create a <xref:System.Data.Common.DbProviderFactory> instance and pass it information about the data provider, the `DbProviderFactory` can determine the correct, strongly typed connection object to return based on the information it has been provided.</span></span>  
  
 <span data-ttu-id="a1d90-105">.NET Framework バージョン 4 以降では、<xref:System.Data.Odbc>、<xref:System.Data.OleDb>、<xref:System.Data.SqlClient>、および <xref:System.Data.OracleClient> などのデータ プロバイダーは machine.config ファイルに表示されなくなりますが、カスタム プロバイダーは表示されます。</span><span class="sxs-lookup"><span data-stu-id="a1d90-105">Beginning in the .NET Framework version 4, data providers such as <xref:System.Data.Odbc>, <xref:System.Data.OleDb>, <xref:System.Data.SqlClient>, and <xref:System.Data.OracleClient> are no longer listed in machine.config file, but custom providers will continue to be listed there.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1d90-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1d90-106">In This Section</span></span>  
 [<span data-ttu-id="a1d90-107">ファクトリ モデルの概要</span><span class="sxs-lookup"><span data-stu-id="a1d90-107">Factory Model Overview</span></span>](../../../../docs/framework/data/adonet/factory-model-overview.md)  
 <span data-ttu-id="a1d90-108">ファクトリ デザイン パターンとプログラミング インターフェイスの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="a1d90-108">Provides an overview of the factory design pattern and programming interface.</span></span>  
  
 [<span data-ttu-id="a1d90-109">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="a1d90-109">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 <span data-ttu-id="a1d90-110">インストールされているデータ プロバイダーの一覧を取得したり、<xref:System.Data.Common.DbConnection> から `DbProviderFactory` を作成したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1d90-110">Demonstrates how to list the installed data providers and create a <xref:System.Data.Common.DbConnection> from a `DbProviderFactory`.</span></span>  
  
 [<span data-ttu-id="a1d90-111">DbConnection、DbCommand、および DbException</span><span class="sxs-lookup"><span data-stu-id="a1d90-111">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 <span data-ttu-id="a1d90-112"><xref:System.Data.Common.DbCommand> と <xref:System.Data.Common.DbDataReader> の作成方法のほか、<xref:System.Data.Common.DbException> を使ったデータ エラーの処理方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1d90-112">Demonstrates how to create a <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbDataReader>, and how to handle data errors using <xref:System.Data.Common.DbException>.</span></span>  
  
 [<span data-ttu-id="a1d90-113">DbDataAdapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="a1d90-113">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 <span data-ttu-id="a1d90-114"><xref:System.Data.Common.DbCommandBuilder> と <xref:System.Data.Common.DbDataAdapter> を使用して、データを取得したり変更したりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1d90-114">Demonstrates how to use a <xref:System.Data.Common.DbCommandBuilder> with a <xref:System.Data.Common.DbDataAdapter> to retrieve and modify data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d90-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1d90-115">See Also</span></span>  
 [<span data-ttu-id="a1d90-116">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="a1d90-116">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="a1d90-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a1d90-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
