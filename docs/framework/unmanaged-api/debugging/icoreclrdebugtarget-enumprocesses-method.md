---
title: "ICoreClrDebugTarget::EnumProcesses メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumProcesses
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8296b4b137032400ee172b6d3670bc1a53dbe60d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="a5c0a-102">ICoreClrDebugTarget::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="a5c0a-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>
<span data-ttu-id="a5c0a-103">リモート コンピューターで実行されているプロセスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5c0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5c0a-104">Syntax</span></span>  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5c0a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5c0a-105">Parameters</span></span>  
 `pcProcs`  
 <span data-ttu-id="a5c0a-106">[out] `ppProcs` に返されるプロセス数。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="a5c0a-107">この値は 0 (ゼロ) になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="a5c0a-108">[out]配列[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)をリモート コンピューターで実行中のプロセスを表す構造体。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-108">[out] An array of [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5c0a-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="a5c0a-109">Return Value</span></span>  
 <span data-ttu-id="a5c0a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5c0a-110">S_OK</span></span>  
 <span data-ttu-id="a5c0a-111">成功。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-111">Success.</span></span>  
  
 <span data-ttu-id="a5c0a-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a5c0a-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a5c0a-113">`ppProcs`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="a5c0a-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="a5c0a-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a5c0a-115">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5c0a-116">コメント</span><span class="sxs-lookup"><span data-stu-id="a5c0a-116">Remarks</span></span>  
 <span data-ttu-id="a5c0a-117">このメソッドによって割り当てられたメモリを解放するには、呼び出し、 [icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5c0a-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="a5c0a-118">Requirements</span></span>  
 <span data-ttu-id="a5c0a-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5c0a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5c0a-120">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="a5c0a-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a5c0a-121">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="a5c0a-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a5c0a-122">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a5c0a-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c0a-123">参照</span><span class="sxs-lookup"><span data-stu-id="a5c0a-123">See Also</span></span>  
 [<span data-ttu-id="a5c0a-124">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a5c0a-124">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
