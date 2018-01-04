---
title: "ICorDebugVariableHome::GetArgumentIndex メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetArgumentIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentiIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 739d4d787858f64871269ea9bd467bc49424fbae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="51c0f-102">ICorDebugVariableHome::GetArgumentIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="51c0f-102">ICorDebugVariableHome::GetArgumentIndex Method</span></span>
<span data-ttu-id="51c0f-103">関数の引数のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="51c0f-103">Gets the index of a function argument.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="51c0f-104">Syntax</span></span>  
  
```  
HRESULT GetArgumentIndex(  
    [out] ULONG32* pArgumentIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51c0f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51c0f-105">Parameters</span></span>  
 `pArgumentIndex`  
 <span data-ttu-id="51c0f-106">[out]引数のインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="51c0f-106">[out] A pointer to the argument index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51c0f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="51c0f-107">Return Value</span></span>  
 <span data-ttu-id="51c0f-108">このメソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="51c0f-108">The method returns the following values.</span></span>  
  
|<span data-ttu-id="51c0f-109">[値]</span><span class="sxs-lookup"><span data-stu-id="51c0f-109">Value</span></span>|<span data-ttu-id="51c0f-110">説明</span><span class="sxs-lookup"><span data-stu-id="51c0f-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="51c0f-111">メソッドの呼び出しには、有効な引数インデックスが返されます。</span><span class="sxs-lookup"><span data-stu-id="51c0f-111">The method call returned a valid argument index.</span></span>|  
|`E_FAIL`|<span data-ttu-id="51c0f-112">現在[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)インスタンスがローカル変数を表します。</span><span class="sxs-lookup"><span data-stu-id="51c0f-112">The current [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51c0f-113">コメント</span><span class="sxs-lookup"><span data-stu-id="51c0f-113">Remarks</span></span>  
 <span data-ttu-id="51c0f-114">引数のインデックスは、この引数のメタデータの取得に使用できます。</span><span class="sxs-lookup"><span data-stu-id="51c0f-114">The argument index can be used to retrieve metadata for this argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c0f-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="51c0f-115">Requirements</span></span>  
 <span data-ttu-id="51c0f-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="51c0f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c0f-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51c0f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51c0f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51c0f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51c0f-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c0f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c0f-120">参照</span><span class="sxs-lookup"><span data-stu-id="51c0f-120">See Also</span></span>  
 [<span data-ttu-id="51c0f-121">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51c0f-121">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
