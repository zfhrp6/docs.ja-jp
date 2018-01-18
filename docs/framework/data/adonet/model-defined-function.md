---
title: "モデル定義関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1c9d438840a0b9c15597177ca4e6d870d526756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="model-defined-function"></a><span data-ttu-id="dc7d4-102">モデル定義関数</span><span class="sxs-lookup"><span data-stu-id="dc7d4-102">model-defined function</span></span>
<span data-ttu-id="dc7d4-103">A*モデル定義関数*概念モデルで定義されている関数です。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="dc7d4-104">モデル定義関数の本体はで表現[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)ルール関数とは無関係に表すことのできる、またはデータ ソースでサポートされている言語。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="dc7d4-105">モデル定義関数の定義には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="dc7d4-106">関数名。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-106">A function name.</span></span> <span data-ttu-id="dc7d4-107">(必須)</span><span class="sxs-lookup"><span data-stu-id="dc7d4-107">(Required)</span></span>  
  
-   <span data-ttu-id="dc7d4-108">戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-108">The type of the return value.</span></span> <span data-ttu-id="dc7d4-109">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc7d4-110">戻り値の型が指定されていない場合、戻り値は void になります。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="dc7d4-111">パラメーター情報。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-111">Parameter information.</span></span> <span data-ttu-id="dc7d4-112">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-112">(Optional)</span></span>  
  
-   <span data-ttu-id="dc7d4-113">[Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)関数の本体を定義する式。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="dc7d4-114">モデル定義関数では、出力パラメーターがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="dc7d4-115">この制約は、モデル定義関数を構成できるようにするためにあります。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc7d4-116">例</span><span class="sxs-lookup"><span data-stu-id="dc7d4-116">Example</span></span>  
 <span data-ttu-id="dc7d4-117">下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="dc7d4-118">![発行日付きモデル](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="dc7d4-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="dc7d4-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="dc7d4-120">次の CSDL は、`Book` (上のダイアグラムの) の出版以降の年数を返す概念モデルの関数を定義しています。</span><span class="sxs-lookup"><span data-stu-id="dc7d4-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="dc7d4-121">参照</span><span class="sxs-lookup"><span data-stu-id="dc7d4-121">See Also</span></span>  
 [<span data-ttu-id="dc7d4-122">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="dc7d4-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="dc7d4-123">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="dc7d4-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="dc7d4-124">Entity Data Model: プリミティブ データ型</span><span class="sxs-lookup"><span data-stu-id="dc7d4-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
