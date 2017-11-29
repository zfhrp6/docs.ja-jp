---
title: "ICorDebugMemoryBuffer::GetSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a21198c70512af703e106870d1bc3f7882d62fe9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="743c2-102">ICorDebugMemoryBuffer::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="743c2-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="743c2-103">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="743c2-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="743c2-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="743c2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="743c2-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="743c2-106">[out] メモリ バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="743c2-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="743c2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="743c2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="743c2-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="743c2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="743c2-109">要件</span><span class="sxs-lookup"><span data-stu-id="743c2-109">Requirements</span></span>  
 <span data-ttu-id="743c2-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="743c2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="743c2-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="743c2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="743c2-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="743c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="743c2-113">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="743c2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743c2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="743c2-114">See Also</span></span>  
 [<span data-ttu-id="743c2-115">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="743c2-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="743c2-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="743c2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
