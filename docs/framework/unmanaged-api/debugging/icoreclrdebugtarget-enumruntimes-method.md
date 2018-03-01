---
title: "ICoreClrDebugTarget::EnumRuntimes メソッド"
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
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a242d95785cf4421d30f716ac2987e42681aaef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="bc69a-102">ICoreClrDebugTarget::EnumRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="bc69a-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="bc69a-103">リモート コンピューターで実行されている指定のプロセスの共通言語ランタイム (CLR: Common Language Runtime) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="bc69a-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc69a-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc69a-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc69a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc69a-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="bc69a-106">[in] ランタイムを列挙するプロセスの内部プロセス ID。</span><span class="sxs-lookup"><span data-stu-id="bc69a-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="bc69a-107">これになります`m_dwInternalID`から、対応する[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc69a-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="bc69a-108">[out] `ppRuntimes` に返されるランタイム数。</span><span class="sxs-lookup"><span data-stu-id="bc69a-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="bc69a-109">この値は 0 (ゼロ) になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="bc69a-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="bc69a-110">[out]配列[CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)ランタイムを表す構造体は、リモート ターゲット プロセスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="bc69a-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc69a-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="bc69a-111">Return Value</span></span>  
 <span data-ttu-id="bc69a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bc69a-112">S_OK</span></span>  
 <span data-ttu-id="bc69a-113">成功。</span><span class="sxs-lookup"><span data-stu-id="bc69a-113">Success.</span></span>  
  
 <span data-ttu-id="bc69a-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bc69a-114">S_FALSE</span></span>  
 <span data-ttu-id="bc69a-115">`dwInternalProcessID` が、コンピューターで実行されているどのプロセスにも一致しません。多くの場合、プロセスが既に終了していることが原因です。</span><span class="sxs-lookup"><span data-stu-id="bc69a-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="bc69a-116">`pcRuntimes` と `ppRuntimes` は null になります。</span><span class="sxs-lookup"><span data-stu-id="bc69a-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="bc69a-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bc69a-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="bc69a-118">`ppRuntimes`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="bc69a-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="bc69a-119">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="bc69a-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="bc69a-120">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bc69a-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc69a-121">コメント</span><span class="sxs-lookup"><span data-stu-id="bc69a-121">Remarks</span></span>  
 <span data-ttu-id="bc69a-122">このメソッドによって割り当てられたメモリを解放するには、呼び出し、 [icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bc69a-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc69a-123">必要条件</span><span class="sxs-lookup"><span data-stu-id="bc69a-123">Requirements</span></span>  
 <span data-ttu-id="bc69a-124">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bc69a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc69a-125">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="bc69a-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="bc69a-126">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="bc69a-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="bc69a-127">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="bc69a-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc69a-128">参照</span><span class="sxs-lookup"><span data-stu-id="bc69a-128">See Also</span></span>  
 [<span data-ttu-id="bc69a-129">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bc69a-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
