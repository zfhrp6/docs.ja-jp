---
title: ICorDebugLoadedModule::GetBaseAddress メソッド
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412637"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="d3cf0-102">ICorDebugLoadedModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="d3cf0-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="d3cf0-103">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d3cf0-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3cf0-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3cf0-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3cf0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3cf0-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="d3cf0-106">[out] 読み込まれたモジュールのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3cf0-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3cf0-107">コメント</span><span class="sxs-lookup"><span data-stu-id="d3cf0-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3cf0-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3cf0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3cf0-109">要件</span><span class="sxs-lookup"><span data-stu-id="d3cf0-109">Requirements</span></span>  
 <span data-ttu-id="d3cf0-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3cf0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3cf0-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3cf0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3cf0-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3cf0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3cf0-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3cf0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3cf0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3cf0-114">See Also</span></span>  
 [<span data-ttu-id="d3cf0-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3cf0-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="d3cf0-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3cf0-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
