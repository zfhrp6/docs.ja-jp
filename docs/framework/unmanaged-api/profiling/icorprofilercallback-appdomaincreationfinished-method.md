---
title: "ICorProfilerCallback::AppDomainCreationFinished メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f779e5a7b0b38558593e84c26b33784383765ca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="5df6a-102">ICorProfilerCallback::AppDomainCreationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="5df6a-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="5df6a-103">アプリケーション ドメインが作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5df6a-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df6a-104">構文</span><span class="sxs-lookup"><span data-stu-id="5df6a-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="5df6a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5df6a-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="5df6a-106">[in]作成されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="5df6a-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="5df6a-107">[in]アプリケーション ドメインの作成が正常に完了したかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="5df6a-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5df6a-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5df6a-108">Remarks</span></span>  
 <span data-ttu-id="5df6a-109">アプリケーション ID が、情報の要求までの有効な`AppDomainCreationFinished`メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5df6a-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="5df6a-110">アプリケーション ドメインの読み込みの一部が後に続ける可能性があります、`AppDomainCreationFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="5df6a-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="5df6a-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="5df6a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5df6a-112">ただし、成功 HRESULT で`hrStatus`のみのアプリケーション ドメインの作成の最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5df6a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df6a-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="5df6a-113">Requirements</span></span>  
 <span data-ttu-id="5df6a-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5df6a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df6a-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5df6a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5df6a-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5df6a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5df6a-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df6a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df6a-118">参照</span><span class="sxs-lookup"><span data-stu-id="5df6a-118">See Also</span></span>  
 [<span data-ttu-id="5df6a-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5df6a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
