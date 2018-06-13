---
title: SQL Server における XML データ
ms.date: 03/30/2017
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
ms.openlocfilehash: 026d839eb5b3a6152d993aa74dda6be1fe233148
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358740"
---
# <a name="xml-data-in-sql-server"></a><span data-ttu-id="c8cc9-102">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="c8cc9-102">XML Data in SQL Server</span></span>
<span data-ttu-id="c8cc9-103">SQL Server は、.NET Framework 内部の SQLXML の機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-103">SQL Server exposes the functionality of SQLXML inside the .NET Framework.</span></span> <span data-ttu-id="c8cc9-104">開発者は、SQL Server のインスタンスから XML データにアクセスし、データを .NET Framework 環境に持ち込んで処理し、更新を SQL Server に送り返すアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-104">Developers can write applications that access XML data from an instance of SQL Server, bring the data into the .NET Framework environment, process the data, and send the updates back to SQL Server.</span></span> <span data-ttu-id="c8cc9-105">SQL Server では、XML データをデータ ストレージなどの目的に、あるいはデータを取得するときのパラメーター値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-105">XML data can be used in several ways in SQL Server, including data storage, and as parameter values for retrieving data.</span></span> <span data-ttu-id="c8cc9-106">**SqlXml** .NET Framework のクラスは、SQL Server 内で XML 列に格納されているデータを操作するため、クライアント側のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-106">The **SqlXml** class in the .NET Framework provides the client-side support for working with data stored in an XML column within SQL Server.</span></span> <span data-ttu-id="c8cc9-107">詳細については、SQL Server オンライン ブックの「SQLXML マネージ クラス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-107">For more information, see "SQLXML Managed Classes" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c8cc9-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c8cc9-108">In This Section</span></span>  
 [<span data-ttu-id="c8cc9-109">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="c8cc9-109">SQL XML Column Values</span></span>](../../../../../docs/framework/data/adonet/sql/sql-xml-column-values.md)  
 <span data-ttu-id="c8cc9-110">SQL Server から XML データを取得し、使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-110">Demonstrates how to retrieve and work with XML data retrieved from SQL Server.</span></span>  
  
 [<span data-ttu-id="c8cc9-111">パラメーターとしての XML 値の指定</span><span class="sxs-lookup"><span data-stu-id="c8cc9-111">Specifying XML Values as Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/specifying-xml-values-as-parameters.md)  
 <span data-ttu-id="c8cc9-112">コマンドに XML データをパラメーターとして渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8cc9-112">Demonstrates how to pass XML data as a parameter to a command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8cc9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8cc9-113">See Also</span></span>  
 [<span data-ttu-id="c8cc9-114">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c8cc9-114">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="c8cc9-115">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="c8cc9-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
