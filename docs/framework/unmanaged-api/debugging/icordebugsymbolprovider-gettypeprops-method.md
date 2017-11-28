---
title: "ICorDebugSymbolProvider::GetTypeProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba736caf8d8d823a4cb56c75aa2202ad616983fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="8b3ef-102">ICorDebugSymbolProvider::GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8b3ef-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="8b3ef-103">Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数など、型のプロパティに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b3ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b3ef-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b3ef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b3ef-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="8b3ef-106">[in] vtable の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="8b3ef-107">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="8b3ef-108">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="8b3ef-109">[out] [out] 返される `signature` 配列のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="8b3ef-110">[out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b3ef-111">コメント</span><span class="sxs-lookup"><span data-stu-id="8b3ef-111">Remarks</span></span>  
 <span data-ttu-id="8b3ef-112">型に必要なサイズを取得する`signature`配列は、設定、`cbSignature`引数を 0 にし、`signature`に**null**です。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="8b3ef-113">このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b3ef-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b3ef-115">要件</span><span class="sxs-lookup"><span data-stu-id="8b3ef-115">Requirements</span></span>  
 <span data-ttu-id="8b3ef-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8b3ef-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b3ef-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b3ef-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b3ef-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b3ef-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b3ef-119">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b3ef-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3ef-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b3ef-120">See Also</span></span>  
 [<span data-ttu-id="8b3ef-121">GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8b3ef-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [<span data-ttu-id="8b3ef-122">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b3ef-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="8b3ef-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b3ef-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
