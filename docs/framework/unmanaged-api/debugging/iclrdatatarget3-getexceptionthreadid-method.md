---
title: "ICLRDataTarget3::GetExceptionThreadID メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionThreadID
api_location: mscordbi.dll
api_type: COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f8b2e7c764eb5d7694633be7fb095b3d19be6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="d78f0-102">ICLRDataTarget3::GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="d78f0-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="d78f0-103">例外をスローしたスレッドの ID を取得するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d78f0-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d78f0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d78f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d78f0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d78f0-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="d78f0-106">[out] 例外をスローしたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="d78f0-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d78f0-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d78f0-107">Return Value</span></span>  
 <span data-ttu-id="d78f0-108">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="d78f0-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="d78f0-109">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d78f0-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="d78f0-110">リターン コード</span><span class="sxs-lookup"><span data-stu-id="d78f0-110">Return code</span></span>|<span data-ttu-id="d78f0-111">説明</span><span class="sxs-lookup"><span data-stu-id="d78f0-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="d78f0-112">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="d78f0-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="d78f0-113">例外の有効なスレッド ID を見つけることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="d78f0-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d78f0-114">コメント</span><span class="sxs-lookup"><span data-stu-id="d78f0-114">Remarks</span></span>  
 <span data-ttu-id="d78f0-115">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="d78f0-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d78f0-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="d78f0-116">Requirements</span></span>  
 <span data-ttu-id="d78f0-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d78f0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d78f0-118">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d78f0-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d78f0-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d78f0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d78f0-120">**.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d78f0-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78f0-121">参照</span><span class="sxs-lookup"><span data-stu-id="d78f0-121">See Also</span></span>  
 [<span data-ttu-id="d78f0-122">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d78f0-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="d78f0-123">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="d78f0-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="d78f0-124">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="d78f0-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
