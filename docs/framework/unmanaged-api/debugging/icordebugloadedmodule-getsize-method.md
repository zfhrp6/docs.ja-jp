---
title: "ICorDebugLoadedModule::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fb340845afac0f5a13f7c4646d11ac057ebd054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="e7da1-102">ICorDebugLoadedModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="e7da1-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="e7da1-103">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="e7da1-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7da1-104">構文</span><span class="sxs-lookup"><span data-stu-id="e7da1-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e7da1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e7da1-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="e7da1-106">[out] 読み込まれたモジュールのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e7da1-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7da1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e7da1-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7da1-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e7da1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7da1-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="e7da1-109">Requirements</span></span>  
 <span data-ttu-id="e7da1-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e7da1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7da1-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7da1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7da1-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7da1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7da1-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7da1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7da1-114">参照</span><span class="sxs-lookup"><span data-stu-id="e7da1-114">See Also</span></span>  
 [<span data-ttu-id="e7da1-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7da1-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="e7da1-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7da1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
