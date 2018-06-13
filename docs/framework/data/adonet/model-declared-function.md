---
title: モデル宣言関数
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: fd573df4eb93b44622bb3b2f611ed726f4700b1d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757243"
---
# <a name="model-declared-function"></a><span data-ttu-id="db47c-102">モデル宣言関数</span><span class="sxs-lookup"><span data-stu-id="db47c-102">model-declared function</span></span>
<span data-ttu-id="db47c-103">A*モデル宣言関数*関数は、概念モデルで宣言されていますが、その概念モデルで定義されていないです。</span><span class="sxs-lookup"><span data-stu-id="db47c-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="db47c-104">この関数は、ホスト環境またはストレージ環境で定義します。</span><span class="sxs-lookup"><span data-stu-id="db47c-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="db47c-105">たとえば、モデル宣言関数は、データベースに定義された関数にマップされ、これによって概念モデルにおけるサーバー側の機能が公開される場合があります。</span><span class="sxs-lookup"><span data-stu-id="db47c-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="db47c-106">モデル宣言関数の宣言には、次の情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="db47c-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="db47c-107">関数の名前。</span><span class="sxs-lookup"><span data-stu-id="db47c-107">The name of the function.</span></span> <span data-ttu-id="db47c-108">(必須)</span><span class="sxs-lookup"><span data-stu-id="db47c-108">(Required)</span></span>  
  
-   <span data-ttu-id="db47c-109">戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="db47c-109">The type of the return value.</span></span> <span data-ttu-id="db47c-110">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="db47c-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db47c-111">戻り値が指定されていない場合、戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="db47c-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="db47c-112">パラメーター名と型を含むパラメーター情報。</span><span class="sxs-lookup"><span data-stu-id="db47c-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="db47c-113">(オプション)。</span><span class="sxs-lookup"><span data-stu-id="db47c-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="db47c-114">例</span><span class="sxs-lookup"><span data-stu-id="db47c-114">Example</span></span>  
 <span data-ttu-id="db47c-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="db47c-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="db47c-116">モデル宣言関数の 1 つの実装では、CSDL で、[関数インポート](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d)です。</span><span class="sxs-lookup"><span data-stu-id="db47c-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="db47c-117">次の CSDL は、関数インポート定義を含むエンティティ コンテナーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="db47c-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="db47c-118">戻り値の型が指定されていないため、関数の戻り値の型は void になります。</span><span class="sxs-lookup"><span data-stu-id="db47c-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="db47c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="db47c-119">See Also</span></span>  
 [<span data-ttu-id="db47c-120">Entity Data Model キーの概念</span><span class="sxs-lookup"><span data-stu-id="db47c-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="db47c-121">Entity Data Model</span><span class="sxs-lookup"><span data-stu-id="db47c-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
