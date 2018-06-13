---
title: ICorProfilerCallback::AppDomainShutdownFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f9f8925630933e2247726f92a93cac67bdc55ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450490"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="3cc84-102">ICorProfilerCallback::AppDomainShutdownFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc84-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="3cc84-103">アプリケーション ドメインが、プロセスからアンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3cc84-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc84-104">構文</span><span class="sxs-lookup"><span data-stu-id="3cc84-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cc84-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cc84-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="3cc84-106">[in]アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="3cc84-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3cc84-107">[in]かどうか、アプリケーション ドメインがアンロードされました正常を示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3cc84-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc84-108">コメント</span><span class="sxs-lookup"><span data-stu-id="3cc84-108">Remarks</span></span>  
 <span data-ttu-id="3cc84-109">値`appDomainId`後情報の要求に対して無効です、 [icorprofilercallback::appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)メソッドを返します。</span><span class="sxs-lookup"><span data-stu-id="3cc84-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="3cc84-110">アプリケーション ドメインをアンロードの一部が後に続ける可能性があります、`AppDomainCreationFinished`コールバック。</span><span class="sxs-lookup"><span data-stu-id="3cc84-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="3cc84-111">失敗を示す HRESULT で`hrStatus`は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="3cc84-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3cc84-112">ただし、成功 HRESULT で`hrStatus`のみのアプリケーション ドメインをアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="3cc84-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc84-113">要件</span><span class="sxs-lookup"><span data-stu-id="3cc84-113">Requirements</span></span>  
 <span data-ttu-id="3cc84-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3cc84-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc84-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cc84-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cc84-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cc84-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cc84-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc84-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc84-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc84-118">See Also</span></span>  
 [<span data-ttu-id="3cc84-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cc84-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
