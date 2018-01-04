---
title: "INotifySink2::OnSyncCallExit メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallExit
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43139e8be9a1f5dfb6513f2ee7768237ae882c69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="9cc3e-102">INotifySink2::OnSyncCallExit メソッド</span><span class="sxs-lookup"><span data-stu-id="9cc3e-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="9cc3e-103">呼び出しが終了するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cc3e-104">構文</span><span class="sxs-lookup"><span data-stu-id="9cc3e-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9cc3e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9cc3e-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="9cc3e-106">[in]終了する呼び出しの ID です。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="9cc3e-107">参照してください[CALL_ID 構造体](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)です。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="9cc3e-108">[out]バッファーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="9cc3e-109">[out]呼び出しバッファーのバイト単位のサイズです。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cc3e-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="9cc3e-110">Return Value</span></span>  
 <span data-ttu-id="9cc3e-111">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="9cc3e-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cc3e-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="9cc3e-112">Requirements</span></span>  
 <span data-ttu-id="9cc3e-113">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9cc3e-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc3e-114">参照</span><span class="sxs-lookup"><span data-stu-id="9cc3e-114">See Also</span></span>  
 [<span data-ttu-id="9cc3e-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cc3e-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="9cc3e-116">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cc3e-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="9cc3e-117">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9cc3e-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
