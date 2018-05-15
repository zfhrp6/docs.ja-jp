---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c128a7dd832376f492573ded49c499232d2bcff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="403c2-102">ICorDebugSymbolProvider::GetMethodParameterSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="403c2-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="403c2-103">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのパラメーター シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="403c2-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="403c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="403c2-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="403c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="403c2-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="403c2-106">[in] メソッドのネイティブ相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="403c2-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="403c2-107">[in] ローカル シンボルの要求数。</span><span class="sxs-lookup"><span data-stu-id="403c2-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="403c2-108">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="403c2-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="403c2-109">[out]ポインター、 [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)メソッドのローカル シンボルを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="403c2-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="403c2-110">コメント</span><span class="sxs-lookup"><span data-stu-id="403c2-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="403c2-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="403c2-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="403c2-112">要件</span><span class="sxs-lookup"><span data-stu-id="403c2-112">Requirements</span></span>  
 <span data-ttu-id="403c2-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="403c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="403c2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="403c2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="403c2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="403c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="403c2-116">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="403c2-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="403c2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="403c2-117">See Also</span></span>  
 [<span data-ttu-id="403c2-118">GetMethodLocalSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="403c2-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)  
 [<span data-ttu-id="403c2-119">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="403c2-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="403c2-120">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="403c2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
