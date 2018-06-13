---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 502e7e0b52bb147b5fe37dcc6e4f6d13d642b6f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417545"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="7175c-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="7175c-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="7175c-103">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="7175c-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7175c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7175c-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7175c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7175c-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="7175c-106">[in] 要求されるシンボル レコードの数。</span><span class="sxs-lookup"><span data-stu-id="7175c-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="7175c-107">[out] メソッドによって取得されたシンボル レコード数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7175c-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="7175c-108">配列へのポインター [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7175c-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7175c-109">コメント</span><span class="sxs-lookup"><span data-stu-id="7175c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7175c-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7175c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7175c-111">要件</span><span class="sxs-lookup"><span data-stu-id="7175c-111">Requirements</span></span>  
 <span data-ttu-id="7175c-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7175c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7175c-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7175c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7175c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7175c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7175c-115">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7175c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7175c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7175c-116">See Also</span></span>  
 [<span data-ttu-id="7175c-117">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7175c-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="7175c-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7175c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
