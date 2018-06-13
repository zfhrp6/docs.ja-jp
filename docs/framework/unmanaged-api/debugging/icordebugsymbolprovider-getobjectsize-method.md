---
title: ICorDebugSymbolProvider::GetObjectSize メソッド
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da526ac133604fa43081f86988459c4238517c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421504"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="9d702-102">ICorDebugSymbolProvider::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="9d702-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="9d702-103">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="9d702-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d702-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d702-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d702-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d702-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="9d702-106">[in] typespec シグネチャのバイト数。</span><span class="sxs-lookup"><span data-stu-id="9d702-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="9d702-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="9d702-107">typeSig</span></span>  
 <span data-ttu-id="9d702-108">[in] typespec シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="9d702-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="9d702-109">[out] オブジェクトのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9d702-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d702-110">コメント</span><span class="sxs-lookup"><span data-stu-id="9d702-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d702-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d702-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d702-112">要件</span><span class="sxs-lookup"><span data-stu-id="9d702-112">Requirements</span></span>  
 <span data-ttu-id="9d702-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9d702-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d702-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d702-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d702-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d702-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d702-116">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d702-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d702-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d702-117">See Also</span></span>  
 [<span data-ttu-id="9d702-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d702-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="9d702-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d702-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
