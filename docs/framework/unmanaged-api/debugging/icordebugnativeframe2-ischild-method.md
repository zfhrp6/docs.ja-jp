---
title: "ICorDebugNativeFrame2::IsChild メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 006543e473ca3b7cc1818b2b4641567ce37f6f0e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="9ef7b-102">ICorDebugNativeFrame2::IsChild メソッド</span><span class="sxs-lookup"><span data-stu-id="9ef7b-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="9ef7b-103">現在のフレームが子フレームであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ef7b-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ef7b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ef7b-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="9ef7b-106">[out]現在のフレームは子フレームであるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ef7b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ef7b-107">Return Value</span></span>  
 <span data-ttu-id="9ef7b-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9ef7b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ef7b-109">HRESULT</span></span>|<span data-ttu-id="9ef7b-110">説明</span><span class="sxs-lookup"><span data-stu-id="9ef7b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ef7b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ef7b-111">S_OK</span></span>|<span data-ttu-id="9ef7b-112">子の状態が正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="9ef7b-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ef7b-113">E_FAIL</span></span>|<span data-ttu-id="9ef7b-114">子の状態は返されませんでした。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="9ef7b-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="9ef7b-115">E_INVALIDARG</span></span>|<span data-ttu-id="9ef7b-116">`pIsChild` が null です。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9ef7b-117">例外</span><span class="sxs-lookup"><span data-stu-id="9ef7b-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ef7b-118">コメント</span><span class="sxs-lookup"><span data-stu-id="9ef7b-118">Remarks</span></span>  
 <span data-ttu-id="9ef7b-119">`IsChild`メソッドを返します。`true`メソッドを呼び出すフレーム オブジェクト別のフレームの子である場合。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="9ef7b-120">大文字と小文字の場合を使用して、 [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)フレームがその親であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef7b-121">要件</span><span class="sxs-lookup"><span data-stu-id="9ef7b-121">Requirements</span></span>  
 <span data-ttu-id="9ef7b-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9ef7b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ef7b-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ef7b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ef7b-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef7b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef7b-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef7b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef7b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ef7b-126">See Also</span></span>  
 [<span data-ttu-id="9ef7b-127">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef7b-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="9ef7b-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ef7b-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9ef7b-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9ef7b-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
