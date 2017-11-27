---
title: "ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f7515479ae5fbe490496bac79f102b02700dcee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="f2c6a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="f2c6a-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="f2c6a-103">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c6a-104">構文</span><span class="sxs-lookup"><span data-stu-id="f2c6a-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2c6a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f2c6a-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="f2c6a-106">[in] 要求されるシンボル レコードの数。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="f2c6a-107">[out] メソッドによって取得されたシンボル レコード数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="f2c6a-108">配列へのポインター [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2c6a-109">コメント</span><span class="sxs-lookup"><span data-stu-id="f2c6a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2c6a-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2c6a-111">要件</span><span class="sxs-lookup"><span data-stu-id="f2c6a-111">Requirements</span></span>  
 <span data-ttu-id="f2c6a-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f2c6a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2c6a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2c6a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2c6a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2c6a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2c6a-115">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2c6a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2c6a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2c6a-116">See Also</span></span>  
 [<span data-ttu-id="f2c6a-117">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2c6a-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="f2c6a-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2c6a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
