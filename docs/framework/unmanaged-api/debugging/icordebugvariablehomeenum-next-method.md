---
title: "ICorDebugVariableHomeEnum::Next メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="d7923-102">ICorDebugVariableHomeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d7923-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="d7923-103">指定した数を取得[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)ローカル変数と関数の引数に関する情報を格納するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d7923-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7923-104">構文</span><span class="sxs-lookup"><span data-stu-id="d7923-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7923-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7923-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d7923-106">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="d7923-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="d7923-107">それぞれが指すポインターの配列、 [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)ローカル変数または関数の引数に関する情報を提供するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7923-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d7923-108">[out]インスタンスの数は、オブジェクトで実際に返されます。</span><span class="sxs-lookup"><span data-stu-id="d7923-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7923-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d7923-109">Return Value</span></span>  
 <span data-ttu-id="d7923-110">このメソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="d7923-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d7923-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7923-111">HRESULT</span></span>|<span data-ttu-id="d7923-112">説明</span><span class="sxs-lookup"><span data-stu-id="d7923-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d7923-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="d7923-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d7923-114">インスタンスの実際の数の取得に反映`pceltFetched`が要求されたインスタンスの数より小さい。</span><span class="sxs-lookup"><span data-stu-id="d7923-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7923-115">コメント</span><span class="sxs-lookup"><span data-stu-id="d7923-115">Remarks</span></span>  
 <span data-ttu-id="d7923-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)メソッドはの最大値を取得`celt`列挙子の現在の位置以降にあるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7923-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="d7923-117">このメソッドが戻るときに`pceltFetched`取得したオブジェクトの実際の数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d7923-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7923-118">要件</span><span class="sxs-lookup"><span data-stu-id="d7923-118">Requirements</span></span>  
 <span data-ttu-id="d7923-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7923-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7923-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7923-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7923-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7923-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7923-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7923-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7923-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7923-123">See Also</span></span>  
 [<span data-ttu-id="d7923-124">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7923-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="d7923-125">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7923-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
