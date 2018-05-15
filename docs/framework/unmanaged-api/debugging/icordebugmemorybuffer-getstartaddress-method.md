---
title: ICorDebugMemoryBuffer::GetStartAddress メソッド
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aa816ea9e6185791e09bcdb0e47c50761a5ebc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="2d782-102">ICorDebugMemoryBuffer::GetStartAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="2d782-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="2d782-103">メモリ バッファーの開始アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d782-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d782-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d782-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d782-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2d782-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2d782-106">[out] メモリ バッファーの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2d782-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d782-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2d782-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2d782-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d782-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d782-109">要件</span><span class="sxs-lookup"><span data-stu-id="2d782-109">Requirements</span></span>  
 <span data-ttu-id="2d782-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d782-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d782-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d782-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d782-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d782-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d782-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d782-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d782-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d782-114">See Also</span></span>  
 [<span data-ttu-id="2d782-115">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d782-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="2d782-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d782-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
