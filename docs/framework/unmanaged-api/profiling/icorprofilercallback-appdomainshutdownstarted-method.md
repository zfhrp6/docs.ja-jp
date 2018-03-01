---
title: "ICorProfilerCallback::AppDomainShutdownStarted メソッド"
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
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14e515ae13e0a445580dabcdfa30253da94fd216
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="839d3-102">ICorProfilerCallback::AppDomainShutdownStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="839d3-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="839d3-103">プロセスから、アプリケーション ドメインがアンロードされることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="839d3-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="839d3-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="839d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="839d3-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="839d3-106">[in]アプリケーションのアセンブリが格納されているドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="839d3-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="839d3-107">コメント</span><span class="sxs-lookup"><span data-stu-id="839d3-107">Remarks</span></span>  
 <span data-ttu-id="839d3-108">値`appDomainId`後に、情報の要求に対して無効です、`AppDomainShutdownStarted`メソッドを返します。-これは、プロファイラーの最後のチャンスをこのアプリケーション ドメインに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="839d3-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="839d3-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="839d3-109">Requirements</span></span>  
 <span data-ttu-id="839d3-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="839d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="839d3-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="839d3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="839d3-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="839d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="839d3-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839d3-114">参照</span><span class="sxs-lookup"><span data-stu-id="839d3-114">See Also</span></span>  
 [<span data-ttu-id="839d3-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="839d3-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
