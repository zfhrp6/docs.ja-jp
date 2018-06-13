---
title: INotifySink2::OnSyncCallReturn メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ebfa886e85cd72c4ea7d088ef345bc9968dec18f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426008"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="c715e-102">INotifySink2::OnSyncCallReturn メソッド</span><span class="sxs-lookup"><span data-stu-id="c715e-102">INotifySink2::OnSyncCallReturn Method</span></span>
<span data-ttu-id="c715e-103">呼び出しが戻るときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c715e-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c715e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c715e-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c715e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c715e-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="c715e-106">[in]返される呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="c715e-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="c715e-107">参照してください[CALL_ID 構造体](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md)です。</span><span class="sxs-lookup"><span data-stu-id="c715e-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="c715e-108">[in]バッファーを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c715e-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="c715e-109">[in]呼び出しバッファーのバイト単位のサイズです。</span><span class="sxs-lookup"><span data-stu-id="c715e-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c715e-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c715e-110">Return Value</span></span>  
 <span data-ttu-id="c715e-111">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="c715e-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c715e-112">要件</span><span class="sxs-lookup"><span data-stu-id="c715e-112">Requirements</span></span>  
 <span data-ttu-id="c715e-113">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="c715e-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c715e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c715e-114">See Also</span></span>  
 [<span data-ttu-id="c715e-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c715e-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="c715e-116">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c715e-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="c715e-117">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c715e-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
