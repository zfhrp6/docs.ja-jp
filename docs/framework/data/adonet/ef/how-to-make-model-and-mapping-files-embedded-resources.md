---
title: モデル ファイルとマッピング ファイルを組み込みリソースにする方法
ms.date: 03/30/2017
ms.assetid: 20dfae4d-e95a-4264-9540-f5ad23b462d3
ms.openlocfilehash: 3fd3c3628e94b4727dfc711e02a9f4b754aa8a2c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-make-model-and-mapping-files-embedded-resources"></a><span data-ttu-id="21939-102">モデル ファイルとマッピング ファイルを組み込みリソースにする方法</span><span class="sxs-lookup"><span data-stu-id="21939-102">How to: Make Model and Mapping Files Embedded Resources</span></span>
<span data-ttu-id="21939-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]アプリケーションの埋め込みリソースとしてモデルおよびマッピング ファイルを展開することができます。</span><span class="sxs-lookup"><span data-stu-id="21939-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to deploy model and mapping files as embedded resources of an application.</span></span> <span data-ttu-id="21939-104">モデル ファイルとマッピング ファイルが組み込まれたアセンブリは、エンティティ接続と同じアプリケーション ドメインに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="21939-104">The assembly with the embedded model and mapping files must be loaded in the same application domain as the entity connection.</span></span> <span data-ttu-id="21939-105">詳細については、「[Connection Strings (接続文字列)](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21939-105">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span> <span data-ttu-id="21939-106">既定では、[!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ツールによって、モデル ファイルとマッピング ファイルが組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="21939-106">By default, the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] tools embed the model and mapping files.</span></span> <span data-ttu-id="21939-107">モデル ファイルとマッピング ファイルを手動で定義する場合は、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] アプリケーションと共にモデル ファイルとマッピング ファイルが組み込みリソースとして確実に配置されるように、この手順を使用します。</span><span class="sxs-lookup"><span data-stu-id="21939-107">When you manually define the model and mapping files, use this procedure to ensure that the files are deployed as embedded resources together with an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21939-108">組み込みリソースを保持するには、モデル ファイルとマッピング ファイルを変更するたびに、この手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="21939-108">To maintain embedded resources, you must repeat this procedure whenever the model and mapping files are modified.</span></span>  
  
### <a name="to-embed-model-and-mapping-files"></a><span data-ttu-id="21939-109">モデル ファイルとマッピング ファイルを組み込むには</span><span class="sxs-lookup"><span data-stu-id="21939-109">To embed model and mapping files</span></span>  
  
1.  <span data-ttu-id="21939-110">**ソリューション エクスプ ローラー**、概念 (.csdl) ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="21939-110">In **Solution Explorer**, select the conceptual (.csdl) file.</span></span>  
  
2.  <span data-ttu-id="21939-111">**プロパティ**ペインで、設定**ビルド アクション**に**埋め込まれたリソース**です。</span><span class="sxs-lookup"><span data-stu-id="21939-111">In the **Properties** pane, set **Build Action** to **Embedded Resource**.</span></span>  
  
3.  <span data-ttu-id="21939-112">ストレージ (.ssdl) ファイルとマッピング (.msl) ファイルに対して手順 1. と手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="21939-112">Repeat steps 1 and 2 for the storage (.ssdl) file and the mapping (.msl) file.</span></span>  
  
4.  <span data-ttu-id="21939-113">**ソリューション エクスプ ローラー**、App.config ファイルをダブルクリックし、変更、`Metadata`内のパラメーター、`connectionString`属性のいずれかに基づいて、次の形式。</span><span class="sxs-lookup"><span data-stu-id="21939-113">In **Solution Explorer**, double-click the App.config file and then modify the `Metadata` parameter in the `connectionString` attribute based on one of the following formats:</span></span>  
  
    -   <span data-ttu-id="21939-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="21939-114">`Metadata=` `res://<assemblyFullName>/<resourceName>;`</span></span>  
  
    -   <span data-ttu-id="21939-115">`Metadata=` `res://*/<resourceName>;`</span><span class="sxs-lookup"><span data-stu-id="21939-115">`Metadata=` `res://*/<resourceName>;`</span></span>  
  
    -   `Metadata=res://*;`  
  
     <span data-ttu-id="21939-116">詳細については、「[Connection Strings (接続文字列)](../../../../../docs/framework/data/adonet/ef/connection-strings.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="21939-116">For more information, see [Connection Strings](../../../../../docs/framework/data/adonet/ef/connection-strings.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="21939-117">例</span><span class="sxs-lookup"><span data-stu-id="21939-117">Example</span></span>  
 <span data-ttu-id="21939-118">埋め込みモデルとマッピング ファイルを参照して次の接続文字列、 [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)です。</span><span class="sxs-lookup"><span data-stu-id="21939-118">The following connection string references embedded model and mapping files for the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="21939-119">この接続文字列は、プロジェクトの App.config ファイルに格納されています。</span><span class="sxs-lookup"><span data-stu-id="21939-119">This connection string is stored in the project's App.config file.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="21939-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="21939-120">See Also</span></span>  
 [<span data-ttu-id="21939-121">モデリングとマッピング</span><span class="sxs-lookup"><span data-stu-id="21939-121">Modeling and Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [<span data-ttu-id="21939-122">接続文字列を定義する方法</span><span class="sxs-lookup"><span data-stu-id="21939-122">How to: Define the Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)  
 [<span data-ttu-id="21939-123">EntityConnection の接続文字列を作成する方法</span><span class="sxs-lookup"><span data-stu-id="21939-123">How to: Build an EntityConnection Connection String</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
 [<span data-ttu-id="21939-124">ADO.NET Entity Data Model ツール</span><span class="sxs-lookup"><span data-stu-id="21939-124">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
