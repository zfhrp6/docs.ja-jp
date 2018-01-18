---
title: "SQL Server における XML データ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9849d319-f518-4e3d-a7cd-f8fdcaaa1d4d
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 75d81a79b549d877467cde427265fb4c65f27caf
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="xml-data-in-sql-server"></a><span data-ttu-id="e9f1d-102">SQL Server における XML データ</span><span class="sxs-lookup"><span data-stu-id="e9f1d-102">XML Data in SQL Server</span></span>
<span data-ttu-id="e9f1d-103">SQL Server は、.NET Framework 内部の SQLXML の機能を公開します。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-103">SQL Server exposes the functionality of SQLXML inside the .NET Framework.</span></span> <span data-ttu-id="e9f1d-104">開発者は、SQL Server のインスタンスから XML データにアクセスし、データを .NET Framework 環境に持ち込んで処理し、更新を SQL Server に送り返すアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-104">Developers can write applications that access XML data from an instance of SQL Server, bring the data into the .NET Framework environment, process the data, and send the updates back to SQL Server.</span></span> <span data-ttu-id="e9f1d-105">SQL Server では、XML データをデータ ストレージなどの目的に、あるいはデータを取得するときのパラメーター値として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-105">XML data can be used in several ways in SQL Server, including data storage, and as parameter values for retrieving data.</span></span> <span data-ttu-id="e9f1d-106">**SqlXml** .NET Framework のクラスは、SQL Server 内で XML 列に格納されているデータを操作するため、クライアント側のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-106">The **SqlXml** class in the .NET Framework provides the client-side support for working with data stored in an XML column within SQL Server.</span></span> <span data-ttu-id="e9f1d-107">詳細については、SQL Server オンライン ブックの「SQLXML マネージ クラス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-107">For more information, see "SQLXML Managed Classes" in SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e9f1d-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e9f1d-108">In This Section</span></span>  
 [<span data-ttu-id="e9f1d-109">SQL XML 列値</span><span class="sxs-lookup"><span data-stu-id="e9f1d-109">SQL XML Column Values</span></span>](../../../../../docs/framework/data/adonet/sql/sql-xml-column-values.md)  
 <span data-ttu-id="e9f1d-110">SQL Server から XML データを取得し、使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-110">Demonstrates how to retrieve and work with XML data retrieved from SQL Server.</span></span>  
  
 [<span data-ttu-id="e9f1d-111">パラメーターとしての XML 値の指定</span><span class="sxs-lookup"><span data-stu-id="e9f1d-111">Specifying XML Values as Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/specifying-xml-values-as-parameters.md)  
 <span data-ttu-id="e9f1d-112">コマンドに XML データをパラメーターとして渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9f1d-112">Demonstrates how to pass XML data as a parameter to a command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9f1d-113">参照</span><span class="sxs-lookup"><span data-stu-id="e9f1d-113">See Also</span></span>  
 [<span data-ttu-id="e9f1d-114">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e9f1d-114">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="e9f1d-115">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="e9f1d-115">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
