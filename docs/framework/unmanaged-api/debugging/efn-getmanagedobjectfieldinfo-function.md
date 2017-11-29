---
title: "_EFN_GetManagedObjectFieldInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectFieldInfo
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectFieldInfo
helpviewer_keywords: _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c3df09c9107b683381f21891a1001140c493a024
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="0f0ce-102">_EFN_GetManagedObjectFieldInfo 関数</span><span class="sxs-lookup"><span data-stu-id="0f0ce-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="0f0ce-103">指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f0ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f0ce-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f0ce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f0ce-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="0f0ce-106">[in]デバッグ クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="0f0ce-107">[in]マネージ オブジェクトのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="0f0ce-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="0f0ce-108">szFieldName</span></span>  
 <span data-ttu-id="0f0ce-109">[in]フィールド名にマネージ オブジェクトのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0f0ce-110">[out]フィールドの値。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-110">[out] The field value.</span></span> <span data-ttu-id="0f0ce-111">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="0f0ce-112">[out]オフセット`objAddr`フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="0f0ce-113">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f0ce-114">コメント</span><span class="sxs-lookup"><span data-stu-id="0f0ce-114">Remarks</span></span>  
 <span data-ttu-id="0f0ce-115">オフセットが 0 の場合は、オフセットは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="0f0ce-116">ない場合マネージ コードのスレッドで現在のコンテキストで、関数は、0xa0 の設備値と 0x1000 のエラー コードとマネージを返します。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f0ce-117">要件</span><span class="sxs-lookup"><span data-stu-id="0f0ce-117">Requirements</span></span>  
 <span data-ttu-id="0f0ce-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f0ce-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f0ce-119">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="0f0ce-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0f0ce-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f0ce-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0ce-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f0ce-121">See Also</span></span>  
 [<span data-ttu-id="0f0ce-122">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0f0ce-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
