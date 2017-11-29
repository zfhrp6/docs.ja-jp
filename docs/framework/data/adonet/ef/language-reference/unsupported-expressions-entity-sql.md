---
title: "サポートされていない式 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e79da7e-e78a-413c-8fb0-f3f9cd84f579
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c18c726a962d9a29a3dace1ebd5c2073637bb4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unsupported-expressions-entity-sql"></a><span data-ttu-id="93fa7-102">サポートされていない式 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="93fa7-102">Unsupported Expressions (Entity SQL)</span></span>
<span data-ttu-id="93fa7-103">このトピックでは、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] でサポートされていない [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 式について説明します。</span><span class="sxs-lookup"><span data-stu-id="93fa7-103">This topic describes [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] expressions that are not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="93fa7-104">詳細については、次を参照してください。[エンティティの SQL と TRANSACT-SQL の異なる](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="93fa7-104">For more information, see [How Entity SQL Differs from Transact-SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md).</span></span>  
  
## <a name="quantified-predicates"></a><span data-ttu-id="93fa7-105">定量化された述語</span><span class="sxs-lookup"><span data-stu-id="93fa7-105">Quantified Predicates</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="93fa7-106"> では、次の形式のコンストラクターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="93fa7-106"> allows constructs of the following form:</span></span>  
  
```  
sal > all (select salary from employees)  
sal > any (select salary from employees)  
```  
  
 <span data-ttu-id="93fa7-107">ただし、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、このようなコンストラクターがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="93fa7-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)], however, does not support such constructs.</span></span> <span data-ttu-id="93fa7-108">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、これに相当する式を次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="93fa7-108">Equivalent expressions can be written in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] as follows:</span></span>  
  
```  
not exists(select 0 from employees as e where sal > e.salary)  
exists(select 0 from employees as e where sal > e.salary)  
```  
  
## <a name="-operator"></a><span data-ttu-id="93fa7-109">* 演算子</span><span class="sxs-lookup"><span data-stu-id="93fa7-109">* Operator</span></span>  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]<span data-ttu-id="93fa7-110"> では、すべての列を投影する必要があることを示すために、SELECT 句で * 演算子を使用できます。これは [!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="93fa7-110"> supports the use of the * operator in the SELECT clause to indicate that all columns should be projected out. This is not supported in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93fa7-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="93fa7-111">See Also</span></span>  
 [<span data-ttu-id="93fa7-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="93fa7-112">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="93fa7-113">TRANSACT-SQL における Entity SQL の違い</span><span class="sxs-lookup"><span data-stu-id="93fa7-113">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)
