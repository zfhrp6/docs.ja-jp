---
title: "ICorProfilerObjectEnum::Clone メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Clone
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e077115863ab3371570463d0bfd9244b69888f9e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="61ae9-102">ICorProfilerObjectEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="61ae9-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="61ae9-103">これのコピーに対するインターフェイス ポインターを取得[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="61ae9-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ae9-104">構文</span><span class="sxs-lookup"><span data-stu-id="61ae9-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61ae9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61ae9-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="61ae9-106">[out]さらに、このコピーを指すインターフェイス ポインターへのポインター`ICorProfilerObjectEnum`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="61ae9-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="61ae9-107">コピーは、この 1 つから個別に独自の列挙状態を維持します。</span><span class="sxs-lookup"><span data-stu-id="61ae9-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="61ae9-108">ただし、そのコピーの最初のカーソル位置はこの列挙子の現在のカーソル位置と同じなります。</span><span class="sxs-lookup"><span data-stu-id="61ae9-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ae9-109">要件</span><span class="sxs-lookup"><span data-stu-id="61ae9-109">Requirements</span></span>  
 <span data-ttu-id="61ae9-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="61ae9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ae9-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61ae9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61ae9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61ae9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ae9-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ae9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ae9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="61ae9-114">See Also</span></span>  
 [<span data-ttu-id="61ae9-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="61ae9-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
