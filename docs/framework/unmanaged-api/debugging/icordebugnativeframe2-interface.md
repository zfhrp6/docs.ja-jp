---
title: "ICorDebugNativeFrame2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2
helpviewer_keywords: ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c33eaa36313f0cf6aae904761fb40bb2dbf9d753
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="001ba-102">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="001ba-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="001ba-103">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="001ba-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="001ba-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="001ba-104">Methods</span></span>  
  
|<span data-ttu-id="001ba-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="001ba-105">Method</span></span>|<span data-ttu-id="001ba-106">説明</span><span class="sxs-lookup"><span data-stu-id="001ba-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="001ba-107">IsChild メソッド</span><span class="sxs-lookup"><span data-stu-id="001ba-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="001ba-108">現在のフレームが子フレームであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="001ba-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="001ba-109">IsMatchingParentFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="001ba-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="001ba-110">指定したフレームが現在のフレームの親であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="001ba-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="001ba-111">GetStackParameterSize メソッド</span><span class="sxs-lookup"><span data-stu-id="001ba-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="001ba-112">X86 オペレーティング システム上のスタック上には、パラメーターの合計サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="001ba-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="001ba-113">コメント</span><span class="sxs-lookup"><span data-stu-id="001ba-113">Remarks</span></span>  
 <span data-ttu-id="001ba-114">このインターフェイスは、"ICorDebugNativeFrame"インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="001ba-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="001ba-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="001ba-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="001ba-116">要件</span><span class="sxs-lookup"><span data-stu-id="001ba-116">Requirements</span></span>  
 <span data-ttu-id="001ba-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="001ba-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="001ba-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="001ba-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="001ba-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="001ba-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="001ba-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="001ba-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="001ba-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="001ba-121">See Also</span></span>  
    
 [<span data-ttu-id="001ba-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="001ba-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="001ba-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="001ba-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
