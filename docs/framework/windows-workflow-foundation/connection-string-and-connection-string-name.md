---
title: 接続文字列と接続文字列名
ms.date: 03/30/2017
ms.assetid: 473e7a3c-c88a-4a01-914a-bea82ba42866
ms.openlocfilehash: ab063710dcf5705fdb0055e34ea57fe24da891a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511931"
---
# <a name="connection-string-and-connection-string-name"></a><span data-ttu-id="c379d-102">接続文字列と接続文字列名</span><span class="sxs-lookup"><span data-stu-id="c379d-102">Connection String and Connection String Name</span></span>
<span data-ttu-id="c379d-103">**接続文字列**プロパティは、SQL Workflow Instance Store が永続性データベースへの接続に使用する接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="c379d-103">**Connection String** property specifies the connection string that the SQL Workflow Instance Store should use to connect to a persistence database.</span></span> <span data-ttu-id="c379d-104">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c379d-104">This parameter is an optional parameter.</span></span> <span data-ttu-id="c379d-105">**接続文字列名**プロパティは、SQL Workflow Instance Store が永続性データベースへの接続に使用する名前付き接続文字列の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c379d-105">**Connection String Name** property specifies the name of the named connection string that the SQL Workflow Instance Store should use to connect to the persistence database.</span></span> <span data-ttu-id="c379d-106">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c379d-106">This parameter is an optional parameter.</span></span> <span data-ttu-id="c379d-107">既定の名前付き接続文字列を使用するには、SQL Workflow Instance Store したくない場合は、接続文字列名プロパティまたは接続文字列プロパティの値を指定する必要があります**DefaultSqlWorkflowInstanceStoreConnectionString**.</span><span class="sxs-lookup"><span data-stu-id="c379d-107">You should specify a value for the Connection String Name property or the Connection String property if you do not want the SQL Workflow Instance Store to use the default named connection string **DefaultSqlWorkflowInstanceStoreConnectionString**.</span></span>
