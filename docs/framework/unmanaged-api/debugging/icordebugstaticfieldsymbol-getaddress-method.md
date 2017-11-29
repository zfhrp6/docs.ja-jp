---
title: "ICorDebugStaticFieldSymbol::GetAddress メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20c0c934772625d27057957d00e53fb4b485c4fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="197cd-102">ICorDebugStaticFieldSymbol::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="197cd-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="197cd-103">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="197cd-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="197cd-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="197cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="197cd-105">Parameters</span></span>  
 <span data-ttu-id="197cd-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="197cd-106">pRVA</span></span>  
 <span data-ttu-id="197cd-107">[out] 静的フィールドの相対仮想アドレス (RVA) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="197cd-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="197cd-108">コメント</span><span class="sxs-lookup"><span data-stu-id="197cd-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="197cd-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="197cd-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="197cd-110">要件</span><span class="sxs-lookup"><span data-stu-id="197cd-110">Requirements</span></span>  
 <span data-ttu-id="197cd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="197cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="197cd-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="197cd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="197cd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="197cd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="197cd-114">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="197cd-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="197cd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="197cd-115">See Also</span></span>  
 [<span data-ttu-id="197cd-116">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="197cd-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="197cd-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="197cd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
