---
title: ICorDebugLoadedModule::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413232"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="7b7d5-102">ICorDebugLoadedModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="7b7d5-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="7b7d5-103">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b7d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b7d5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b7d5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7b7d5-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="7b7d5-106">[out] 読み込まれたモジュールのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b7d5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7b7d5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b7d5-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b7d5-109">要件</span><span class="sxs-lookup"><span data-stu-id="7b7d5-109">Requirements</span></span>  
 <span data-ttu-id="7b7d5-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b7d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b7d5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b7d5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b7d5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b7d5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b7d5-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b7d5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b7d5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b7d5-114">See Also</span></span>  
 [<span data-ttu-id="7b7d5-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b7d5-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="7b7d5-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b7d5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
