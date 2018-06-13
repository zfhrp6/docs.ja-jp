---
title: ICorDebugMemoryBuffer::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf95e0b5c8d4ae942bb428f53d4e58313e0e78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414753"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="f7b5a-102">ICorDebugMemoryBuffer::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f7b5a-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="f7b5a-103">メモリ バッファーのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="f7b5a-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b5a-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7b5a-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7b5a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f7b5a-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="f7b5a-106">[out] メモリ バッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f7b5a-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7b5a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f7b5a-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7b5a-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f7b5a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7b5a-109">要件</span><span class="sxs-lookup"><span data-stu-id="f7b5a-109">Requirements</span></span>  
 <span data-ttu-id="f7b5a-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7b5a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7b5a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7b5a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7b5a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7b5a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7b5a-113">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b5a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b5a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7b5a-114">See Also</span></span>  
 [<span data-ttu-id="f7b5a-115">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7b5a-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="f7b5a-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7b5a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
