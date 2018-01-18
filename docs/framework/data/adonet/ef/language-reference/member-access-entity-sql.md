---
title: "である必要があります。 (メンバー アクセス) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c90c908e567ac05f344292411978ff0c80919a65
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="d5b5e-103">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-103">.</span></span> <span data-ttu-id="d5b5e-104">(メンバー アクセス) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d5b5e-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="d5b5e-105">ドット演算子 (.) は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]メンバー アクセス演算子です。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="d5b5e-106">メンバー アクセス演算子を使用すると、構造型概念モデル型のインスタンスのプロパティ値またはフィールド値を生成できます。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b5e-107">構文</span><span class="sxs-lookup"><span data-stu-id="d5b5e-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5b5e-108">引数</span><span class="sxs-lookup"><span data-stu-id="d5b5e-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d5b5e-109">構造型概念モデル型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="d5b5e-110">オブジェクト インスタンスに属するプロパティまたはフィールド。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b5e-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d5b5e-111">Remarks</span></span>  
 <span data-ttu-id="d5b5e-112">ドット (.) 演算子は、複合型またはエンティティ型のプロパティの抽出と同様に、レコードからフィールドを抽出するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="d5b5e-113">たとえば、Name 型の n が Person 型のメンバーであり、p が Person 型のインスタンスである場合、p.n は有効なメンバー アクセス式として Name 型の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="d5b5e-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="d5b5e-114">参照</span><span class="sxs-lookup"><span data-stu-id="d5b5e-114">See Also</span></span>  
 [<span data-ttu-id="d5b5e-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="d5b5e-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
