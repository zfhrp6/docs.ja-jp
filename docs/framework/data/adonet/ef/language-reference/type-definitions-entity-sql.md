---
title: "型定義 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3a1321ae85b1f4952334672e7333e80094ad2e31
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="59d35-102">型定義 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="59d35-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="59d35-103">型定義は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline 関数の宣言ステートメントで使用されます。</span><span class="sxs-lookup"><span data-stu-id="59d35-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59d35-104">コメント</span><span class="sxs-lookup"><span data-stu-id="59d35-104">Remarks</span></span>  
 <span data-ttu-id="59d35-105">インライン関数の宣言ステートメントから成る、[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)キーワードの後に (かっこ内のパラメーター定義リスト続けて関数名 (たとえば、"MyAvg") を表す識別子例では、"dues Collection(Decimal)") です。</span><span class="sxs-lookup"><span data-stu-id="59d35-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="59d35-106">パラメーター定義リストは、0 個以上のパラメーター定義で構成されます。</span><span class="sxs-lookup"><span data-stu-id="59d35-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="59d35-107">各パラメーター定義は、識別子 (関数のパラメーターの名前。例 : "dues") とそれに続く型定義 (例 : "Collection(Decimal)") で構成されます。</span><span class="sxs-lookup"><span data-stu-id="59d35-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="59d35-108">型定義は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="59d35-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="59d35-109">識別子の型 ("Int32" や "AdventureWorks.Order" など)。</span><span class="sxs-lookup"><span data-stu-id="59d35-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="59d35-110">キーワード `COLLECTION` とそれに続くかっこに囲まれた別の型定義 (例 : "Collection(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="59d35-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="59d35-111">キーワード ROW とそれに続くかっこに囲まれたプロパティ定義リスト (例 : "Row(x AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="59d35-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="59d35-112">プロパティの定義などの形式である"`identifier type_definition`、 `identifier type_definition`,..."です。</span><span class="sxs-lookup"><span data-stu-id="59d35-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="59d35-113">キーワード REF とそれに続くかっこに囲まれた識別子の型 (例 : "Ref(AdventureWorks.Order)")。</span><span class="sxs-lookup"><span data-stu-id="59d35-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="59d35-114">REF 型定義演算子は、引数としてエンティティ型を必要とします。</span><span class="sxs-lookup"><span data-stu-id="59d35-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="59d35-115">引数としてプリミティブ型を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="59d35-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="59d35-116">型定義を入れ子にできます (例 : "Collection(Row(x Ref(AdventureWorks.Order)))")。</span><span class="sxs-lookup"><span data-stu-id="59d35-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="59d35-117">型定義のオプションは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="59d35-117">The type definition options are:</span></span>  
  
-   <span data-ttu-id="59d35-118">`IdentifierName supported_type`、または </span><span class="sxs-lookup"><span data-stu-id="59d35-118">`IdentifierName supported_type`, or</span></span>  
  
-   <span data-ttu-id="59d35-119">`IdentifierName` COLLECTION(`type_definition`)、または</span><span class="sxs-lookup"><span data-stu-id="59d35-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
-   <span data-ttu-id="59d35-120">`IdentifierName` ROW(`property_definition`)、または</span><span class="sxs-lookup"><span data-stu-id="59d35-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
-   <span data-ttu-id="59d35-121">`IdentifierName` REF(`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="59d35-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="59d35-122">プロパティ定義オプションは、`IdentifierName type_definition` です。</span><span class="sxs-lookup"><span data-stu-id="59d35-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="59d35-123">現在の名前空間で使用されている型であれば、いずれもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="59d35-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="59d35-124">これには、プリミティブ型とエンティティ型の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59d35-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="59d35-125">サポートされるエンティティ型は、現在の名前空間で使用されているエンティティ型だけを参照します。</span><span class="sxs-lookup"><span data-stu-id="59d35-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="59d35-126">これには、プリミティブ型は含まれません。</span><span class="sxs-lookup"><span data-stu-id="59d35-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="59d35-127">例</span><span class="sxs-lookup"><span data-stu-id="59d35-127">Examples</span></span>  
 <span data-ttu-id="59d35-128">簡単な型定義の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59d35-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="59d35-129">COLLECTION 型定義の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59d35-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="59d35-130">ROW 型定義の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59d35-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="59d35-131">REF 型定義の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="59d35-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="59d35-132">参照</span><span class="sxs-lookup"><span data-stu-id="59d35-132">See Also</span></span>  
 [<span data-ttu-id="59d35-133">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="59d35-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="59d35-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="59d35-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
