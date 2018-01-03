---
title: "名前空間 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f97b28bce20fa71f82942fa5f123d7c2ac6616a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="f720b-102">名前空間 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f720b-102">Namespaces (Entity SQL)</span></span>
<span data-ttu-id="f720b-103">型名、エンティティ セット、関数など、グローバル識別子の名前の競合を防ぐために、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には名前空間が採用されています。</span><span class="sxs-lookup"><span data-stu-id="f720b-103">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="f720b-104">名前空間のサポートで[!INCLUDE[esql](../../../../../../includes/esql-md.md)]で名前空間のサポートに似ていますが、[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f720b-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="f720b-105">次の例のように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、2 とおりの形式で USING 句を指定できます。1 つは略称的な別名を指定する修飾名前空間、もう 1 つは別名を指定しない非修飾名前空間です。</span><span class="sxs-lookup"><span data-stu-id="f720b-105">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="f720b-106">名前解決ルール</span><span class="sxs-lookup"><span data-stu-id="f720b-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="f720b-107">識別子は、ローカル スコープで解決できない場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]はグローバル スコープ (名前空間) 内で名前を検索しようとしています。</span><span class="sxs-lookup"><span data-stu-id="f720b-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f720b-108"> は、まず識別子 (プレフィックス) と修飾名前空間の 1 つを照合します。</span><span class="sxs-lookup"><span data-stu-id="f720b-108"> first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="f720b-109">場合は、一致がある[!INCLUDE[esql](../../../../../../includes/esql-md.md)]を指定した名前空間内の識別子の残りの部分を解決しようとします。</span><span class="sxs-lookup"><span data-stu-id="f720b-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="f720b-110">一致が見つからなかった場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f720b-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="f720b-111">次に、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]すべて非修飾の名前空間 (プロローグ内で指定された) 識別子を検索しようとしています。</span><span class="sxs-lookup"><span data-stu-id="f720b-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="f720b-112">その識別子が属している名前空間を一意に特定できた場合は、その場所が返されます。</span><span class="sxs-lookup"><span data-stu-id="f720b-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="f720b-113">同じ識別子に対して複数の名前空間が見つかった場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f720b-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="f720b-114">、識別子の名前空間が識別されない場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]次の外側のスコープに名前を渡します (、<xref:System.Data.Common.DbCommand>または<xref:System.Data.Common.DbConnection>オブジェクト)、次の例に示すように。</span><span class="sxs-lookup"><span data-stu-id="f720b-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="f720b-115">.NET Framework との違い</span><span class="sxs-lookup"><span data-stu-id="f720b-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="f720b-116">[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] では、部分修飾名前空間を使用できますが、</span><span class="sxs-lookup"><span data-stu-id="f720b-116">In the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="f720b-117"> では使用できません。</span><span class="sxs-lookup"><span data-stu-id="f720b-117"> does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="f720b-118">ADO.NET の使用法</span><span class="sxs-lookup"><span data-stu-id="f720b-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="f720b-119">クエリは、ADO.NET の <xref:System.Data.Common.DbCommand> オブジェクトを使用して表されます。</span><span class="sxs-lookup"><span data-stu-id="f720b-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="f720b-120"><xref:System.Data.Common.DbCommand> オブジェクトは、<xref:System.Data.Common.DbConnection> オブジェクトに対して構築できます。</span><span class="sxs-lookup"><span data-stu-id="f720b-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="f720b-121">名前空間を <xref:System.Data.Common.DbCommand> オブジェクトや <xref:System.Data.Common.DbConnection> オブジェクトの一部として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f720b-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="f720b-122">場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別子を解決できないクエリ自体内で外部の名前空間がプローブされます (同様のルールに基づく)。</span><span class="sxs-lookup"><span data-stu-id="f720b-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f720b-123">参照</span><span class="sxs-lookup"><span data-stu-id="f720b-123">See Also</span></span>  
 [<span data-ttu-id="f720b-124">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="f720b-124">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="f720b-125">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="f720b-125">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
