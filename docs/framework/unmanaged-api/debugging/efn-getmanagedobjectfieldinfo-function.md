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
ms.workload: dotnet
ms.openlocfilehash: 4822cab8816e97bd1d13c36ea7b63dc9a6f679d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="31c3c-102">_EFN_GetManagedObjectFieldInfo 関数</span><span class="sxs-lookup"><span data-stu-id="31c3c-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="31c3c-103">指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="31c3c-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31c3c-104">構文</span><span class="sxs-lookup"><span data-stu-id="31c3c-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31c3c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31c3c-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="31c3c-106">[in]デバッグ クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="31c3c-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="31c3c-107">[in]マネージ オブジェクトのポインター。</span><span class="sxs-lookup"><span data-stu-id="31c3c-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="31c3c-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="31c3c-108">szFieldName</span></span>  
 <span data-ttu-id="31c3c-109">[in]フィールド名にマネージ オブジェクトのポインター。</span><span class="sxs-lookup"><span data-stu-id="31c3c-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="31c3c-110">[out]フィールドの値。</span><span class="sxs-lookup"><span data-stu-id="31c3c-110">[out] The field value.</span></span> <span data-ttu-id="31c3c-111">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="31c3c-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="31c3c-112">[out]オフセット`objAddr`フィールドにします。</span><span class="sxs-lookup"><span data-stu-id="31c3c-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="31c3c-113">このパラメーターには、null を指定できます。</span><span class="sxs-lookup"><span data-stu-id="31c3c-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31c3c-114">コメント</span><span class="sxs-lookup"><span data-stu-id="31c3c-114">Remarks</span></span>  
 <span data-ttu-id="31c3c-115">オフセットが 0 の場合は、オフセットは書き込まれません。</span><span class="sxs-lookup"><span data-stu-id="31c3c-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="31c3c-116">ない場合マネージ コードのスレッドで現在のコンテキストで、関数は、0xa0 の設備値と 0x1000 のエラー コードとマネージを返します。</span><span class="sxs-lookup"><span data-stu-id="31c3c-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31c3c-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="31c3c-117">Requirements</span></span>  
 <span data-ttu-id="31c3c-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="31c3c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31c3c-119">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="31c3c-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="31c3c-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31c3c-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c3c-121">参照</span><span class="sxs-lookup"><span data-stu-id="31c3c-121">See Also</span></span>  
 [<span data-ttu-id="31c3c-122">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="31c3c-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
