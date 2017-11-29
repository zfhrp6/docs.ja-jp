---
title: "ICorDebugSymbolProvider::GetObjectSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="3d92b-102">ICorDebugSymbolProvider::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="3d92b-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="3d92b-103">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="3d92b-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d92b-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d92b-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d92b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d92b-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="3d92b-106">[in] typespec シグネチャのバイト数。</span><span class="sxs-lookup"><span data-stu-id="3d92b-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="3d92b-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="3d92b-107">typeSig</span></span>  
 <span data-ttu-id="3d92b-108">[in] typespec シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="3d92b-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="3d92b-109">[out] オブジェクトのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3d92b-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d92b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="3d92b-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d92b-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d92b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d92b-112">要件</span><span class="sxs-lookup"><span data-stu-id="3d92b-112">Requirements</span></span>  
 <span data-ttu-id="3d92b-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3d92b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d92b-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d92b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d92b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d92b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d92b-116">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d92b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d92b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d92b-117">See Also</span></span>  
 [<span data-ttu-id="3d92b-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d92b-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="3d92b-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d92b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
