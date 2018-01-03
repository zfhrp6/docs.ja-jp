---
title: "モデル宣言関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2f5c7828dc1ea79a548b35109b428da05c2b4560
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="model-declared-function"></a><span data-ttu-id="b9dbe-102">モデル宣言関数</span><span class="sxs-lookup"><span data-stu-id="b9dbe-102">model-declared function</span></span>
<span data-ttu-id="b9dbe-103">A*モデル宣言関数*関数は、概念モデルで宣言されていますが、その概念モデルで定義されていないです。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="b9dbe-104">この関数は、ホスト環境またはストレージ環境で定義します。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="b9dbe-105">たとえば、モデル宣言関数は、データベースに定義された関数にマップされ、これによって概念モデルにおけるサーバー側の機能が公開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="b9dbe-106">モデル宣言関数の宣言には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="b9dbe-107">関数の名前。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-107">The name of the function.</span></span> <span data-ttu-id="b9dbe-108">(必須)</span><span class="sxs-lookup"><span data-stu-id="b9dbe-108">(Required)</span></span>  
  
-   <span data-ttu-id="b9dbe-109">戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-109">The type of the return value.</span></span> <span data-ttu-id="b9dbe-110">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b9dbe-111">戻り値が指定されていない場合、戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="b9dbe-112">パラメーター名と型を含むパラメーター情報。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="b9dbe-113">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9dbe-114">例</span><span class="sxs-lookup"><span data-stu-id="b9dbe-114">Example</span></span>  
 <span data-ttu-id="b9dbe-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b9dbe-116">モデル宣言関数の 1 つの実装では、CSDL で、[関数インポート](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d)です。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="b9dbe-117">次の CSDL は、関数インポート定義を含むエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="b9dbe-118">戻り値の型が指定されていないため、関数の戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="b9dbe-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="b9dbe-119">参照</span><span class="sxs-lookup"><span data-stu-id="b9dbe-119">See Also</span></span>  
 [<span data-ttu-id="b9dbe-120">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="b9dbe-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b9dbe-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="b9dbe-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
