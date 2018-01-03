---
title: "ICorDebugProcess3 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3
helpviewer_keywords: ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 894d3295b83a1971792e6da845f276be486a4ea5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3-interface"></a><span data-ttu-id="73970-102">ICorDebugProcess3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73970-102">ICorDebugProcess3 Interface</span></span>
<span data-ttu-id="73970-103">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="73970-103">Controls custom debugger notifications.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73970-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="73970-104">Methods</span></span>  
  
|<span data-ttu-id="73970-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="73970-105">Method</span></span>|<span data-ttu-id="73970-106">説明</span><span class="sxs-lookup"><span data-stu-id="73970-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73970-107">SetEnableCustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="73970-107">SetEnableCustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|<span data-ttu-id="73970-108">有効にし、指定した型のカスタムのデバッガー通知を無効にします。</span><span class="sxs-lookup"><span data-stu-id="73970-108">Enables and disables custom debugger notifications of the specified type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73970-109">コメント</span><span class="sxs-lookup"><span data-stu-id="73970-109">Remarks</span></span>  
 <span data-ttu-id="73970-110">このインターフェイスは、ICorDebugProcess および ICorDebugProcess2 インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="73970-110">This interface logically extends the ICorDebugProcess and ICorDebugProcess2 interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73970-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="73970-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73970-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="73970-112">Requirements</span></span>  
 <span data-ttu-id="73970-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73970-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73970-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73970-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73970-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73970-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73970-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73970-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73970-117">参照</span><span class="sxs-lookup"><span data-stu-id="73970-117">See Also</span></span>  
 [<span data-ttu-id="73970-118">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73970-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="73970-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="73970-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
