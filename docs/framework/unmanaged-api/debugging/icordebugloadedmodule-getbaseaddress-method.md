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
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="5cb14-102">ICorDebugLoadedModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="5cb14-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="5cb14-103">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5cb14-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb14-104">構文</span><span class="sxs-lookup"><span data-stu-id="5cb14-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5cb14-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cb14-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="5cb14-106">[out] 読み込まれたモジュールのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5cb14-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cb14-107">コメント</span><span class="sxs-lookup"><span data-stu-id="5cb14-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cb14-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5cb14-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cb14-109">要件</span><span class="sxs-lookup"><span data-stu-id="5cb14-109">Requirements</span></span>  
 <span data-ttu-id="5cb14-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5cb14-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb14-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cb14-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cb14-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cb14-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cb14-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb14-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb14-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cb14-114">See Also</span></span>  
 [<span data-ttu-id="5cb14-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cb14-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="5cb14-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cb14-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
