---
title: "ICorDebugInternalFrame2::IsCloserToLeaf メソッド"
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
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b6b769c25e0cd706eb57965b73d0fcfdcf9b9ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="0b6a8-102">ICorDebugInternalFrame2::IsCloserToLeaf メソッド</span><span class="sxs-lookup"><span data-stu-id="0b6a8-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="0b6a8-103">チェックするかどうか、`this`内部フレームは、指定した ICorDebugFrame オブジェクトよりも、リーフに近づきます。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b6a8-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b6a8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b6a8-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="0b6a8-106">[in]比較するポインター`ICorDebugFrame`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="0b6a8-107">[out]`true`場合、`this`内部フレームがで指定された枠よりも、リーフに近い`pFrameToCompare`、それ以外の`false`します。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b6a8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b6a8-108">Return Value</span></span>  
 <span data-ttu-id="0b6a8-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0b6a8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b6a8-110">HRESULT</span></span>|<span data-ttu-id="0b6a8-111">説明</span><span class="sxs-lookup"><span data-stu-id="0b6a8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b6a8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b6a8-112">S_OK</span></span>|<span data-ttu-id="0b6a8-113">比較が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="0b6a8-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b6a8-114">E_FAIL</span></span>|<span data-ttu-id="0b6a8-115">比較を実行できませんでした。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="0b6a8-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0b6a8-116">E_INVALIDARG</span></span>|<span data-ttu-id="0b6a8-117">`pFrameToCompare` または `pIsCloser` が null です。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b6a8-118">コメント</span><span class="sxs-lookup"><span data-stu-id="0b6a8-118">Remarks</span></span>  
 <span data-ttu-id="0b6a8-119">`IsCloserToLeaf`スタック上の他のフレームを持つ内部フレームをインターリーブのポリシーを実装するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b6a8-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="0b6a8-120">Requirements</span></span>  
 <span data-ttu-id="0b6a8-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0b6a8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6a8-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b6a8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b6a8-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b6a8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b6a8-124">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6a8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6a8-125">参照</span><span class="sxs-lookup"><span data-stu-id="0b6a8-125">See Also</span></span>  
 [<span data-ttu-id="0b6a8-126">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b6a8-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="0b6a8-127">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b6a8-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0b6a8-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0b6a8-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
