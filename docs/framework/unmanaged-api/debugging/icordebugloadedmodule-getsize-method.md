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
ms.openlocfilehash: 29adc45df57c5f31c299dc28b611bcf0599d4aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="ea2ca-102">ICorDebugLoadedModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ea2ca-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="ea2ca-103">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea2ca-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea2ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea2ca-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="ea2ca-106">[out] 読み込まれたモジュールのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2ca-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ea2ca-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea2ca-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea2ca-109">要件</span><span class="sxs-lookup"><span data-stu-id="ea2ca-109">Requirements</span></span>  
 <span data-ttu-id="ea2ca-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea2ca-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2ca-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea2ca-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea2ca-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea2ca-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2ca-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2ca-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2ca-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2ca-114">See Also</span></span>  
 [<span data-ttu-id="ea2ca-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea2ca-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="ea2ca-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea2ca-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
