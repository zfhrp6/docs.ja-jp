---
title: "ICorDebugLoadedModule::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="6979a-102">ICorDebugLoadedModule::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="6979a-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="6979a-103">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="6979a-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6979a-104">構文</span><span class="sxs-lookup"><span data-stu-id="6979a-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6979a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6979a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6979a-106">[in] `szName` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="6979a-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6979a-107">[out] `szName` バッファーに実際に書き込まれた文字数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6979a-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6979a-108">[out] 読み込まれたモジュールの名前が含まれている文字配列。</span><span class="sxs-lookup"><span data-stu-id="6979a-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6979a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6979a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6979a-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6979a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6979a-111">要件</span><span class="sxs-lookup"><span data-stu-id="6979a-111">Requirements</span></span>  
 <span data-ttu-id="6979a-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6979a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6979a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6979a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6979a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6979a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6979a-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6979a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6979a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6979a-116">See Also</span></span>  
 [<span data-ttu-id="6979a-117">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6979a-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="6979a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6979a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
