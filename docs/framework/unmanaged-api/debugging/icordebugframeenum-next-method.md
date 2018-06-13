---
title: ICorDebugFrameEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f049a7cadf1857495e49b9bdc2fecd1b49103af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415484"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="df2a9-102">ICorDebugFrameEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="df2a9-102">ICorDebugFrameEnum::Next Method</span></span>
<span data-ttu-id="df2a9-103">ICorDebugFrame インスタンスの現在位置から指定した数を取得します。</span><span class="sxs-lookup"><span data-stu-id="df2a9-103">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df2a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="df2a9-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df2a9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df2a9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="df2a9-106">[in]数`ICorDebugFrame`を取得するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="df2a9-106">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="df2a9-107">[out]それぞれが指すポインターの配列、`ICorDebugFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="df2a9-107">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="df2a9-108">[out]数へのポインター`ICorDebugFrame`実際に返されるインスタンス。</span><span class="sxs-lookup"><span data-stu-id="df2a9-108">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="df2a9-109">この値を null にすることがある場合`celt`は 1 つです。</span><span class="sxs-lookup"><span data-stu-id="df2a9-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df2a9-110">要件</span><span class="sxs-lookup"><span data-stu-id="df2a9-110">Requirements</span></span>  
 <span data-ttu-id="df2a9-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="df2a9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df2a9-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df2a9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df2a9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df2a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df2a9-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df2a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
