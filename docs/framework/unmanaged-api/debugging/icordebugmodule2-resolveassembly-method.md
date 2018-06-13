---
title: ICorDebugModule2::ResolveAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44a6596807b98e6c8b8624b5df18f78dbf8d0711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417779"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="2cd1d-102">ICorDebugModule2::ResolveAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="2cd1d-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="2cd1d-103">指定したメタデータ トークンによって参照されるアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="2cd1d-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cd1d-104">構文</span><span class="sxs-lookup"><span data-stu-id="2cd1d-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cd1d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2cd1d-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="2cd1d-106">[in]`mdToken`アセンブリが参照する値。</span><span class="sxs-lookup"><span data-stu-id="2cd1d-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="2cd1d-107">[out]アセンブリを表す ICorDebugAssembly オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2cd1d-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cd1d-108">コメント</span><span class="sxs-lookup"><span data-stu-id="2cd1d-108">Remarks</span></span>  
 <span data-ttu-id="2cd1d-109">アセンブリは既に読み込まれていない場合場合`ResolveAssembly`が呼び出されると、HRESULT CORDBG_E_CANNOT_RESOLVE_ASSEMBLY の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="2cd1d-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cd1d-110">要件</span><span class="sxs-lookup"><span data-stu-id="2cd1d-110">Requirements</span></span>  
 <span data-ttu-id="2cd1d-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2cd1d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cd1d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cd1d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cd1d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cd1d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cd1d-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cd1d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
