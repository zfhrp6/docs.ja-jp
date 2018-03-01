---
title: "ICLRDataTarget::GetCurrentThreadID メソッド"
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
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fd2c39b20b823e18232081d1655a6770bafccc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="592a5-102">ICLRDataTarget::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="592a5-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="592a5-103">現在のスレッドのオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="592a5-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="592a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="592a5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="592a5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="592a5-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="592a5-106">[out]ターゲット プロセスの現在のスレッドのオペレーティング システム識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="592a5-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="592a5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="592a5-107">Remarks</span></span>  
 <span data-ttu-id="592a5-108">ターゲット プロセスでは、現在のスレッドが存在しない場合、`GetCurrentThreadID`メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="592a5-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="592a5-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="592a5-109">Requirements</span></span>  
 <span data-ttu-id="592a5-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="592a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="592a5-111">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="592a5-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="592a5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="592a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="592a5-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="592a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="592a5-114">参照</span><span class="sxs-lookup"><span data-stu-id="592a5-114">See Also</span></span>  
 [<span data-ttu-id="592a5-115">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="592a5-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
