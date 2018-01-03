---
title: "ICorDebugModule::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 64be936277b0ebe04248ae2913a882b628ee363f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="6f43f-102">ICorDebugModule::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="6f43f-102">ICorDebugModule::GetName Method</span></span>
<span data-ttu-id="6f43f-103">モジュールのファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="6f43f-103">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f43f-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f43f-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f43f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f43f-105">Parameters</span></span>  
 `cchname`  
 <span data-ttu-id="6f43f-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6f43f-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6f43f-107">[in]返される名前の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f43f-107">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="6f43f-108">[out]返される名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="6f43f-108">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f43f-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6f43f-109">Remarks</span></span>  
 <span data-ttu-id="6f43f-110">`GetName`メソッドは、モジュールのファイル名には、ディスク上の名前が一致する場合は S_OK HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="6f43f-110">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="6f43f-111">`GetName`場合は、名前は、用意された、動的またはメモリ内のモジュールの場合のように、S_FALSE HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="6f43f-111">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f43f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="6f43f-112">Requirements</span></span>  
 <span data-ttu-id="6f43f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f43f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f43f-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f43f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f43f-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f43f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f43f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f43f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f43f-117">参照</span><span class="sxs-lookup"><span data-stu-id="6f43f-117">See Also</span></span>  
    
 
