---
title: "ICorProfilerCallback::AppDomainShutdownStarted メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainShutdownStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5eff8807b5f50708b8d8e4935052de89f59eb5d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="4cb5e-102">ICorProfilerCallback::AppDomainShutdownStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="4cb5e-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="4cb5e-103">プロセスから、アプリケーション ドメインがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4cb5e-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cb5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="4cb5e-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4cb5e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4cb5e-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="4cb5e-106">[in]アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="4cb5e-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cb5e-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4cb5e-107">Remarks</span></span>  
 <span data-ttu-id="4cb5e-108">値`appDomainId`後に、情報の要求に対して無効です、`AppDomainShutdownStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスをこのアプリケーション ドメインに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="4cb5e-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cb5e-109">要件</span><span class="sxs-lookup"><span data-stu-id="4cb5e-109">Requirements</span></span>  
 <span data-ttu-id="4cb5e-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4cb5e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4cb5e-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4cb5e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4cb5e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4cb5e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4cb5e-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cb5e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb5e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4cb5e-114">See Also</span></span>  
 [<span data-ttu-id="4cb5e-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4cb5e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
