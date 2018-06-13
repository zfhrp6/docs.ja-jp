---
title: INotifySink2::OnSyncCallOut メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a38c35f0acd47c9183c043e1c436413a309b138
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426076"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="168fb-102">INotifySink2::OnSyncCallOut メソッド</span><span class="sxs-lookup"><span data-stu-id="168fb-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="168fb-103">呼び出しを抜けるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="168fb-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="168fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="168fb-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="168fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="168fb-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="168fb-106">[in]呼び出しの ID です。参照してください[CALL_ID 構造体](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)です。</span><span class="sxs-lookup"><span data-stu-id="168fb-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="168fb-107">[out]バッファーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="168fb-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="168fb-108">[out]呼び出しバッファーのバイト単位のサイズです。</span><span class="sxs-lookup"><span data-stu-id="168fb-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="168fb-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="168fb-109">Return Value</span></span>  
 <span data-ttu-id="168fb-110">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="168fb-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="168fb-111">要件</span><span class="sxs-lookup"><span data-stu-id="168fb-111">Requirements</span></span>  
 <span data-ttu-id="168fb-112">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="168fb-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168fb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="168fb-113">See Also</span></span>  
 [<span data-ttu-id="168fb-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="168fb-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="168fb-115">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="168fb-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="168fb-116">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="168fb-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
