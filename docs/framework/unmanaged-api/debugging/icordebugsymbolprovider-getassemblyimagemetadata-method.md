---
title: "ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff6b26dd9a0ed56e5194dc997270cf9d2dbe42b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="c9ffe-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="c9ffe-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="c9ffe-103">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ffe-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9ffe-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9ffe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9ffe-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="c9ffe-106">[out]アドレスへのポインター、 [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)マージされたアセンブリのメタデータのアドレスとサイズに関する情報を含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ffe-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c9ffe-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9ffe-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9ffe-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="c9ffe-109">Requirements</span></span>  
 <span data-ttu-id="c9ffe-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9ffe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ffe-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9ffe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9ffe-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9ffe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9ffe-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ffe-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ffe-114">参照</span><span class="sxs-lookup"><span data-stu-id="c9ffe-114">See Also</span></span>  
 [<span data-ttu-id="c9ffe-115">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9ffe-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c9ffe-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9ffe-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
