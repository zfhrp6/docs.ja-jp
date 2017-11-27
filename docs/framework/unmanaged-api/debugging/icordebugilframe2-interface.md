---
title: ICorDebugILFrame2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2
helpviewer_keywords: ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 759232d5c1e5bdf00c85145fa0fc3d69743c13f5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe2-interface1"></a><span data-ttu-id="7d541-102">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="7d541-102">ICorDebugILFrame2 Interface1</span></span>
<span data-ttu-id="7d541-103">ICorDebugILFrame インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="7d541-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d541-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7d541-104">Methods</span></span>  
  
|<span data-ttu-id="7d541-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7d541-105">Method</span></span>|<span data-ttu-id="7d541-106">説明</span><span class="sxs-lookup"><span data-stu-id="7d541-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d541-107">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="7d541-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="7d541-108">含む ICorDebugTypeEnum オブジェクトを取得、<xref:System.Type>このフレーム内のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="7d541-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="7d541-109">RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="7d541-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="7d541-110">新しい MSIL オフセットを指定することによって編集された関数を再マップします。</span><span class="sxs-lookup"><span data-stu-id="7d541-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d541-111">コメント</span><span class="sxs-lookup"><span data-stu-id="7d541-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d541-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7d541-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d541-113">要件</span><span class="sxs-lookup"><span data-stu-id="7d541-113">Requirements</span></span>  
 <span data-ttu-id="7d541-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d541-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d541-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d541-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d541-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d541-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d541-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d541-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d541-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d541-118">See Also</span></span>  
 [<span data-ttu-id="7d541-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d541-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
