---
title: "ICorProfilerObjectEnum::Clone メソッド"
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
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d8e478eb9165b4aa5bf019f02f4f128931d928b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="d8361-102">ICorProfilerObjectEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="d8361-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="d8361-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d8361-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8361-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8361-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8361-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8361-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d8361-106">[out]さらに、このコピーを指すインターフェイス ポインターへのポインター`ICorProfilerObjectEnum`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="d8361-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="d8361-107">コピーは、この 1 つから個別に独自の列挙状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="d8361-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="d8361-108">ただし、そのコピーの最初のカーソル位置はこの列挙子の現在のカーソル位置と同じなります。</span><span class="sxs-lookup"><span data-stu-id="d8361-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8361-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="d8361-109">Requirements</span></span>  
 <span data-ttu-id="d8361-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8361-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8361-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8361-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8361-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8361-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8361-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8361-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8361-114">参照</span><span class="sxs-lookup"><span data-stu-id="d8361-114">See Also</span></span>  
 [<span data-ttu-id="d8361-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8361-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
