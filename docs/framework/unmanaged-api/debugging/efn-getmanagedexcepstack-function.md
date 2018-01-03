---
title: "_EFN_GetManagedExcepStack 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedExcepStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedExcepStack
helpviewer_keywords: _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edcd93bec29c6f0fef3b0bed4b8293efead3932d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="348ed-102">_EFN_GetManagedExcepStack 関数</span><span class="sxs-lookup"><span data-stu-id="348ed-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="348ed-103">指定したマネージ例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="348ed-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="348ed-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="348ed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="348ed-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="348ed-106">[in]デバッグ中のクライアント。</span><span class="sxs-lookup"><span data-stu-id="348ed-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="348ed-107">[in]派生したマネージ オブジェクトのポインター、<xref:System.Exception>です。</span><span class="sxs-lookup"><span data-stu-id="348ed-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="348ed-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="348ed-108">szStackString</span></span>  
 <span data-ttu-id="348ed-109">[out]返される文字列。</span><span class="sxs-lookup"><span data-stu-id="348ed-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="348ed-110">[out]文字列バッファー内の文字の数。</span><span class="sxs-lookup"><span data-stu-id="348ed-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="348ed-111">コメント</span><span class="sxs-lookup"><span data-stu-id="348ed-111">Remarks</span></span>  
 <span data-ttu-id="348ed-112">ない場合マネージ コードのスレッドで現在のコンテキストで、関数は、0xa0 の設備値と 0x1000 のエラー コードとマネージを返します。</span><span class="sxs-lookup"><span data-stu-id="348ed-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="348ed-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="348ed-113">Requirements</span></span>  
 <span data-ttu-id="348ed-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="348ed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="348ed-115">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="348ed-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="348ed-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="348ed-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348ed-117">参照</span><span class="sxs-lookup"><span data-stu-id="348ed-117">See Also</span></span>  
 [<span data-ttu-id="348ed-118">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="348ed-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
