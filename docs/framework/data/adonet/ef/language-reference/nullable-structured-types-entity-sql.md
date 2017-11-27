---
title: "NULL 値が許容される構造化型 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ac7405aea459d51154ac25171bc76d637a94bf81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="65145-102">NULL 値が許容される構造化型 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="65145-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="65145-103">構造化型の `null` インスタンスは、存在しないインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="65145-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="65145-104">これは、すべてのプロパティの値が `null` であるインスタンスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="65145-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="65145-105">このトピックでは、NULL 値が許容される構造化型について説明します。この内容には、NULL 値が許容される型、および構造化 NULL 値が許容される型の `null` インスタンスを生成するコード パターンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="65145-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="65145-106">NULL 値が許容される構造化型の種類</span><span class="sxs-lookup"><span data-stu-id="65145-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="65145-107">NULL 値が許容される構造化型には、3 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="65145-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="65145-108">行型。</span><span class="sxs-lookup"><span data-stu-id="65145-108">Row types.</span></span>  
  
-   <span data-ttu-id="65145-109">複合型。</span><span class="sxs-lookup"><span data-stu-id="65145-109">Complex types.</span></span>  
  
-   <span data-ttu-id="65145-110">エンティティ型。</span><span class="sxs-lookup"><span data-stu-id="65145-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="65145-111">構造化型の NULL インスタンスを生成するコード パターン</span><span class="sxs-lookup"><span data-stu-id="65145-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="65145-112">次のシナリオは、`null` インスタンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="65145-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="65145-113">構造化型としての `null` の構造化</span><span class="sxs-lookup"><span data-stu-id="65145-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="65145-114">派生型に対する基本データ型のキャスト</span><span class="sxs-lookup"><span data-stu-id="65145-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="65145-115">false の条件での外部結合</span><span class="sxs-lookup"><span data-stu-id="65145-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="65145-116">--または</span><span class="sxs-lookup"><span data-stu-id="65145-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="65145-117">--または</span><span class="sxs-lookup"><span data-stu-id="65145-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="65145-118">`null` 参照の逆参照</span><span class="sxs-lookup"><span data-stu-id="65145-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="65145-119">空のコレクションからの ANYELEMENT の取得</span><span class="sxs-lookup"><span data-stu-id="65145-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="65145-120">構造化型の `null` インスタンスのチェック</span><span class="sxs-lookup"><span data-stu-id="65145-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="65145-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="65145-121">See Also</span></span>  
 [<span data-ttu-id="65145-122">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="65145-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
