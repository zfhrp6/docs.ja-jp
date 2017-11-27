---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b73274a09ae748cdf1ee33c885de86b1f52c105
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="fecff-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="fecff-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="fecff-103">インスタンスを作成、 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)クラスです。</span><span class="sxs-lookup"><span data-stu-id="fecff-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fecff-104">構文</span><span class="sxs-lookup"><span data-stu-id="fecff-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fecff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fecff-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="fecff-106">パラメーター値</span><span class="sxs-lookup"><span data-stu-id="fecff-106">Parameter Values</span></span>  
 <span data-ttu-id="fecff-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="fecff-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="fecff-108">操作名、戻り値の型、パラメーター情報など、生成されるワークフロー アクティビティで実行される操作を記述します。</span><span class="sxs-lookup"><span data-stu-id="fecff-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="fecff-109">このパラメーターの値を指定する必要があります**null**です。</span><span class="sxs-lookup"><span data-stu-id="fecff-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="fecff-110">これは、メッセージ コントラクトを使用し、1 つのメッセージと共に引数を受け取る同期操作を示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fecff-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="fecff-111">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="fecff-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="fecff-112">*configurationName*</span><span class="sxs-lookup"><span data-stu-id="fecff-112">*configurationName*</span></span>  
  
 <span data-ttu-id="fecff-113">エンドポイント構成名を指定します。</span><span class="sxs-lookup"><span data-stu-id="fecff-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="fecff-114">このパラメーターの値にはできませんか**null**または空です。</span><span class="sxs-lookup"><span data-stu-id="fecff-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="fecff-115">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="fecff-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="fecff-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="fecff-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="fecff-117">操作のサービスの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="fecff-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="fecff-118">このパラメーターの値にはできませんか**null**または空です。</span><span class="sxs-lookup"><span data-stu-id="fecff-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="fecff-119">これらの条件が満たされていない場合、このクラスのコンストラクターと他のメソッドを使用したランタイムの結果は未定義です。</span><span class="sxs-lookup"><span data-stu-id="fecff-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fecff-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="fecff-120">See Also</span></span>  
 [<span data-ttu-id="fecff-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="fecff-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
