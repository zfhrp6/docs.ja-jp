---
title: ICorDebugModule::GetBaseAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10e7da7711cd63579589fda416d0d3a4f777eefe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412545"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="9f3d9-102">ICorDebugModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="9f3d9-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="9f3d9-103">モジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f3d9-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f3d9-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f3d9-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f3d9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f3d9-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9f3d9-106">[out]A`CORDB_ADDRESS`モジュールのベース アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9f3d9-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f3d9-107">コメント</span><span class="sxs-lookup"><span data-stu-id="9f3d9-107">Remarks</span></span>  
 <span data-ttu-id="9f3d9-108">モジュールがネイティブである場合 (モジュールは、ネイティブ イメージ ジェネレーター、NGen.exe によって生成された) の場合は、イメージ、そのベース アドレスは 0 になります。</span><span class="sxs-lookup"><span data-stu-id="9f3d9-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f3d9-109">要件</span><span class="sxs-lookup"><span data-stu-id="9f3d9-109">Requirements</span></span>  
 <span data-ttu-id="9f3d9-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f3d9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f3d9-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f3d9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f3d9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f3d9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f3d9-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f3d9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3d9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f3d9-114">See Also</span></span>  
    
 
