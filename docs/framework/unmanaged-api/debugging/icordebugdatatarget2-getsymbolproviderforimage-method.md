---
title: ICorDebugDataTarget2::GetSymbolProviderForImage メソッド
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cdd2d0b6f6fbc8d3c2b1a14ca05a84d13c56331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411104"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="fcc05-102">ICorDebugDataTarget2::GetSymbolProviderForImage メソッド</span><span class="sxs-lookup"><span data-stu-id="fcc05-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="fcc05-103">モジュールのベース アドレスからそのモジュールのシンボル プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="fcc05-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc05-104">構文</span><span class="sxs-lookup"><span data-stu-id="fcc05-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcc05-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fcc05-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="fcc05-106">[in]A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)モジュールのベース アドレスを表す値です。</span><span class="sxs-lookup"><span data-stu-id="fcc05-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="fcc05-107">[out]アドレスへのポインター、 [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fcc05-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcc05-108">コメント</span><span class="sxs-lookup"><span data-stu-id="fcc05-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc05-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fcc05-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc05-110">要件</span><span class="sxs-lookup"><span data-stu-id="fcc05-110">Requirements</span></span>  
 <span data-ttu-id="fcc05-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fcc05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc05-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcc05-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcc05-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcc05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcc05-114">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc05-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc05-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcc05-115">See Also</span></span>  
 [<span data-ttu-id="fcc05-116">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fcc05-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="fcc05-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fcc05-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
