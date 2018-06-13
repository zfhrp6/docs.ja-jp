---
title: ICorDebugStaticFieldSymbol::GetAddress メソッド
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b877bde80b59b7d2074e4d799653dedd5aaacf39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419254"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="7d829-102">ICorDebugStaticFieldSymbol::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="7d829-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="7d829-103">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="7d829-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d829-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d829-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d829-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d829-105">Parameters</span></span>  
 <span data-ttu-id="7d829-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="7d829-106">pRVA</span></span>  
 <span data-ttu-id="7d829-107">[out] 静的フィールドの相対仮想アドレス (RVA) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7d829-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d829-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7d829-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d829-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d829-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d829-110">要件</span><span class="sxs-lookup"><span data-stu-id="7d829-110">Requirements</span></span>  
 <span data-ttu-id="7d829-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d829-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d829-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d829-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d829-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d829-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d829-114">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d829-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d829-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d829-115">See Also</span></span>  
 [<span data-ttu-id="7d829-116">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d829-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="7d829-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d829-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
