---
title: ICorDebugInternalFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e950847764e695f705aeded0e3804db4b872827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="c2884-102">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="c2884-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="c2884-103">ランタイム内部スタックにフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="c2884-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="c2884-104">このインターフェイスは、ICorDebugFrame インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="c2884-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c2884-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c2884-105">Methods</span></span>  
  
|<span data-ttu-id="c2884-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c2884-106">Method</span></span>|<span data-ttu-id="c2884-107">説明</span><span class="sxs-lookup"><span data-stu-id="c2884-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c2884-108">GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="c2884-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="c2884-109">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="c2884-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2884-110">コメント</span><span class="sxs-lookup"><span data-stu-id="c2884-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2884-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c2884-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2884-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="c2884-112">Requirements</span></span>  
 <span data-ttu-id="c2884-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2884-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2884-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2884-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2884-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2884-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2884-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2884-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2884-117">参照</span><span class="sxs-lookup"><span data-stu-id="c2884-117">See Also</span></span>  
 [<span data-ttu-id="c2884-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2884-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
