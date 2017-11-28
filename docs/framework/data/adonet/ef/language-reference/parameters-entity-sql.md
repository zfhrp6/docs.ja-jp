---
title: "パラメーター (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2a3700b5f9bdc996b147609d86bcaed0ec0bb116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="3de38-102">パラメーター (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3de38-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="3de38-103">パラメーターは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の外部で定義される変数です。通常は、ホスト言語で使用されるバインド API を通じて定義されます。</span><span class="sxs-lookup"><span data-stu-id="3de38-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="3de38-104">それぞれのパラメーターには、名前と型があります。</span><span class="sxs-lookup"><span data-stu-id="3de38-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="3de38-105">クエリ式でパラメーター名が定義されているで (@) 記号をプレフィックスとして。</span><span class="sxs-lookup"><span data-stu-id="3de38-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="3de38-106">これにより、クエリ内で定義されている他の名前 (プロパティ名など) と明確に区別されます。</span><span class="sxs-lookup"><span data-stu-id="3de38-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="3de38-107">パラメーターをバインドするための API は、ホスト言語によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="3de38-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3de38-108">例</span><span class="sxs-lookup"><span data-stu-id="3de38-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="3de38-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3de38-109">See Also</span></span>  
 [<span data-ttu-id="3de38-110">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="3de38-110">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="3de38-111">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="3de38-111">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
