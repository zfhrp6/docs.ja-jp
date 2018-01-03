---
title: "ICorDebugLoadedModule::GetBaseAddress メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d71b1db35a9e2747e7e14787f385f42f98305c61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="3fce7-102">ICorDebugLoadedModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="3fce7-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="3fce7-103">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3fce7-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fce7-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fce7-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fce7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fce7-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="3fce7-106">[out] 読み込まれたモジュールのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3fce7-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fce7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3fce7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fce7-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3fce7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fce7-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="3fce7-109">Requirements</span></span>  
 <span data-ttu-id="3fce7-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3fce7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fce7-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fce7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fce7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fce7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fce7-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fce7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fce7-114">参照</span><span class="sxs-lookup"><span data-stu-id="3fce7-114">See Also</span></span>  
 [<span data-ttu-id="3fce7-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fce7-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="3fce7-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fce7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
