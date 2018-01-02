---
title: "方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2a8bf70468bc2daec054acad577fa4c216cb25e7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-edmgenexe-to-validate-model-and-mapping-files"></a><span data-ttu-id="0ab4d-102">方法: EdmGen.exe を使用してモデル ファイルとマッピング ファイルを検証する</span><span class="sxs-lookup"><span data-stu-id="0ab4d-102">How to: Use EdmGen.exe to Validate Model and Mapping Files</span></span>
<span data-ttu-id="0ab4d-103">このトピックの内容を使用する方法を示しています、 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)モデルおよびマッピング ファイルを検証するツールです。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) tool to validate the model and mapping files.</span></span> <span data-ttu-id="0ab4d-104">詳細については、次を参照してください。 [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-104">For more information, see [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).</span></span>  
  
### <a name="to-validate-the-school-model-using-edmgenexe"></a><span data-ttu-id="0ab4d-105">EdmGen.exe を使用して School モデルを検証するには</span><span class="sxs-lookup"><span data-stu-id="0ab4d-105">To validate the School model using EdmGen.exe</span></span>  
  
1.  <span data-ttu-id="0ab4d-106">School データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-106">Create the School database.</span></span> <span data-ttu-id="0ab4d-107">詳細については、次を参照してください。 [School サンプル データベースを作成する](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)です。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-107">For more information, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).</span></span>  
  
2.  <span data-ttu-id="0ab4d-108">School モデルを生成します。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-108">Generate the School model.</span></span> <span data-ttu-id="0ab4d-109">詳細については、次を参照してください。[する方法: モデル ファイルとマッピング ファイルの生成に使用する EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-109">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3.  <span data-ttu-id="0ab4d-110">コマンド プロンプトで、次のコマンド (改行なし) を実行します。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-110">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0ab4d-111">参照</span><span class="sxs-lookup"><span data-stu-id="0ab4d-111">See Also</span></span>  
 [<span data-ttu-id="0ab4d-112">方法: Entity Framework プロジェクトを手動で構成します。</span><span class="sxs-lookup"><span data-stu-id="0ab4d-112">How to: Manually Configure an Entity Framework Project</span></span>](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [<span data-ttu-id="0ab4d-113">ADO.NET Entity Data Model ツール</span><span class="sxs-lookup"><span data-stu-id="0ab4d-113">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [<span data-ttu-id="0ab4d-114">方法: クエリのパフォーマンスを向上させるためにビューの事前生成</span><span class="sxs-lookup"><span data-stu-id="0ab4d-114">How to: Pre-Generate Views to Improve Query Performance</span></span>](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [<span data-ttu-id="0ab4d-115">方法: EdmGen.exe を使用してオブジェクトレイヤー コードを生成する</span><span class="sxs-lookup"><span data-stu-id="0ab4d-115">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
