---
title: "接続文字列と接続文字列名"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec78d6d8059e19671849ee50ede9b5e64964c362
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="2eae9-102">接続文字列と接続文字列名</span><span class="sxs-lookup"><span data-stu-id="2eae9-102">Connection String and Connection String Name</span></span>
<span data-ttu-id="2eae9-103">**接続文字列**プロパティは、SQL Workflow Instance Store が永続性データベースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="2eae9-103">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="2eae9-104">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2eae9-104">This parameter is an optional parameter.</span></span> <span data-ttu-id="2eae9-105">**接続文字列名**プロパティは、SQL Workflow Instance Store が永続性データベースへの接続に使用する名前付き接続文字列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2eae9-105">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="2eae9-106">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="2eae9-106">This parameter is an optional parameter.</span></span> <span data-ttu-id="2eae9-107">既定の名前付き接続文字列を使用するには、SQL Workflow Instance Store したくない場合は、接続文字列名プロパティまたは接続文字列プロパティの値を指定する必要があります**DefaultSqlWorkflowInstanceStoreConnectionString**.</span><span class="sxs-lookup"><span data-stu-id="2eae9-107">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
