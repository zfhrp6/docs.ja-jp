---
title: "ICLRDataTarget::GetCurrentThreadID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetCurrentThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3820a3f32834f02b60fb33448bcaf8febdc15ce6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="d62d7-102">ICLRDataTarget::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="d62d7-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>
<span data-ttu-id="d62d7-103">現在のスレッドのオペレーティング システムの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d62d7-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d62d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="d62d7-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d62d7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d62d7-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d62d7-106">[out]ターゲット プロセスの現在のスレッドのオペレーティング システム識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d62d7-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d62d7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d62d7-107">Remarks</span></span>  
 <span data-ttu-id="d62d7-108">ターゲット プロセスでは、現在のスレッドが存在しない場合、`GetCurrentThreadID`メソッドが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d62d7-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d62d7-109">要件</span><span class="sxs-lookup"><span data-stu-id="d62d7-109">Requirements</span></span>  
 <span data-ttu-id="d62d7-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d62d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d62d7-111">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d62d7-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d62d7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d62d7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d62d7-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d62d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d62d7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d62d7-114">See Also</span></span>  
 [<span data-ttu-id="d62d7-115">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d62d7-115">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
