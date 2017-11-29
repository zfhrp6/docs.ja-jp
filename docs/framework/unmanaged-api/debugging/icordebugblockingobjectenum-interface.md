---
title: "ICorDebugBlockingObjectEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62da4047029881ddffff5faee9f06072407bfc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="d3ad2-102">ICorDebugBlockingObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3ad2-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="d3ad2-103">一覧については、列挙子を提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="d3ad2-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3ad2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d3ad2-105">Methods</span></span>  
  
|<span data-ttu-id="d3ad2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d3ad2-106">Method</span></span>|<span data-ttu-id="d3ad2-107">説明</span><span class="sxs-lookup"><span data-stu-id="d3ad2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3ad2-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d3ad2-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="d3ad2-109">一覧を列挙[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3ad2-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d3ad2-110">Remarks</span></span>  
 <span data-ttu-id="d3ad2-111">各 `CorDebugBlockingObject` 構造体は、スレッドをブロックしているオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3ad2-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3ad2-113">要件</span><span class="sxs-lookup"><span data-stu-id="d3ad2-113">Requirements</span></span>  
 <span data-ttu-id="d3ad2-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3ad2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ad2-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3ad2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3ad2-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3ad2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3ad2-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ad2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ad2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3ad2-118">See Also</span></span>  
 [<span data-ttu-id="d3ad2-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="d3ad2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d3ad2-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="d3ad2-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
