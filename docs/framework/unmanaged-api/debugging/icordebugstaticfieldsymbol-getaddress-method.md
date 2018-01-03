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
ms.workload: dotnet
ms.openlocfilehash: 5382a0b04a8a4d5adf9745d21b5bbcf629da1df3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="d345b-102">ICorDebugStaticFieldSymbol::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="d345b-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="d345b-103">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d345b-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d345b-104">構文</span><span class="sxs-lookup"><span data-stu-id="d345b-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d345b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d345b-105">Parameters</span></span>  
 <span data-ttu-id="d345b-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="d345b-106">pRVA</span></span>  
 <span data-ttu-id="d345b-107">[out] 静的フィールドの相対仮想アドレス (RVA) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d345b-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d345b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="d345b-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d345b-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d345b-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d345b-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="d345b-110">Requirements</span></span>  
 <span data-ttu-id="d345b-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d345b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d345b-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d345b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d345b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d345b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d345b-114">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d345b-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d345b-115">参照</span><span class="sxs-lookup"><span data-stu-id="d345b-115">See Also</span></span>  
 [<span data-ttu-id="d345b-116">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d345b-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="d345b-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d345b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
