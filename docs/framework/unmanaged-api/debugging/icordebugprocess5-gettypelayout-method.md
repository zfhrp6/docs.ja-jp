---
title: "ICorDebugProcess5::GetTypeLayout メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f36b78558f8a8005735166436ad3dead28992e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="bb750-102">ICorDebugProcess5::GetTypeLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="bb750-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="bb750-103">その型の識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="bb750-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb750-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb750-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb750-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb750-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="bb750-106">[in]A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)トークン レイアウトを持つが必要な型を指定します。</span><span class="sxs-lookup"><span data-stu-id="bb750-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="bb750-107">[out]ポインター、 [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)メモリ内のオブジェクトのレイアウトに関する情報を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="bb750-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb750-108">コメント</span><span class="sxs-lookup"><span data-stu-id="bb750-108">Remarks</span></span>  
 <span data-ttu-id="bb750-109">`ICorDebugProcess5::GetTypeLayout`メソッドに基づくオブジェクトに関する情報を提供するその[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)、他の数値から返される[ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb750-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="bb750-110">によって情報を提供する[COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)メソッドによって設定される構造です。</span><span class="sxs-lookup"><span data-stu-id="bb750-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb750-111">要件</span><span class="sxs-lookup"><span data-stu-id="bb750-111">Requirements</span></span>  
 <span data-ttu-id="bb750-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb750-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb750-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb750-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb750-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb750-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb750-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb750-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb750-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb750-116">See Also</span></span>  
 [<span data-ttu-id="bb750-117">COR_TYPE_LAYOUT 構造体</span><span class="sxs-lookup"><span data-stu-id="bb750-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="bb750-118">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb750-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="bb750-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb750-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
