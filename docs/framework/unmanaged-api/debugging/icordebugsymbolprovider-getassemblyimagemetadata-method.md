---
title: ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bf032f3bf525d2dca535e6f62dd65d5acd8e7f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420990"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="c8631-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="c8631-102">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>
<span data-ttu-id="c8631-103">マージされたアセンブリのメタデータを返します。</span><span class="sxs-lookup"><span data-stu-id="c8631-103">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8631-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8631-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8631-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8631-105">Parameters</span></span>  
 `ppMemoryBuffer`  
 <span data-ttu-id="c8631-106">[out]アドレスへのポインター、 [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)マージされたアセンブリのメタデータのアドレスとサイズに関する情報を含むオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c8631-106">[out] A pointer to the address of an [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8631-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c8631-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8631-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8631-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8631-109">要件</span><span class="sxs-lookup"><span data-stu-id="c8631-109">Requirements</span></span>  
 <span data-ttu-id="c8631-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8631-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8631-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8631-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8631-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8631-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8631-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8631-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8631-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8631-114">See Also</span></span>  
 [<span data-ttu-id="c8631-115">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8631-115">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c8631-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8631-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
