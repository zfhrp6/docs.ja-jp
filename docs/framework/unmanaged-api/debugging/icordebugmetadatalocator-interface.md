---
title: "ICorDebugMetaDataLocator インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator
helpviewer_keywords: ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4611581bd2692d7c2be48adad1db3c495080e776
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="5dccc-102">ICorDebugMetaDataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dccc-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="5dccc-103">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5dccc-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5dccc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5dccc-104">Methods</span></span>  
  
|<span data-ttu-id="5dccc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5dccc-105">Method</span></span>|<span data-ttu-id="5dccc-106">説明</span><span class="sxs-lookup"><span data-stu-id="5dccc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5dccc-107">GetMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="5dccc-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="5dccc-108">デバッガーが要求した操作を完了するために必要となるメタデータが含まれているモジュールの完全パスを返すように、デバッガーに求めます。</span><span class="sxs-lookup"><span data-stu-id="5dccc-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dccc-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5dccc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dccc-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5dccc-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dccc-111">要件</span><span class="sxs-lookup"><span data-stu-id="5dccc-111">Requirements</span></span>  
 <span data-ttu-id="5dccc-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dccc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dccc-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5dccc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5dccc-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dccc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dccc-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dccc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dccc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dccc-116">See Also</span></span>  
 [<span data-ttu-id="5dccc-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dccc-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5dccc-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5dccc-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
