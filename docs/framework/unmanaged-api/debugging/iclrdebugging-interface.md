---
title: "ICLRDebugging インターフェイス"
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
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 325f6adf8fe3a357f903f0cb047a2255ef80e264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="55c35-102">ICLRDebugging インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55c35-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="55c35-103">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="55c35-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55c35-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="55c35-104">Methods</span></span>  
  
|<span data-ttu-id="55c35-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="55c35-105">Method</span></span>|<span data-ttu-id="55c35-106">説明</span><span class="sxs-lookup"><span data-stu-id="55c35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55c35-107">OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="55c35-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="55c35-108">プロセスに読み込まれている共通言語ランタイム (CLR) モジュールに対応する"ICorDebugProcess"インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="55c35-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="55c35-109">CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="55c35-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="55c35-110">ライブラリで提供されているかどうかを判断、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)インターフェイスが使用されているまたは読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="55c35-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55c35-111">コメント</span><span class="sxs-lookup"><span data-stu-id="55c35-111">Remarks</span></span>  
 <span data-ttu-id="55c35-112">インスタンスを取得することができます、`ICLRDebugging`インターフェイスを使用して、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="55c35-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c35-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="55c35-113">Requirements</span></span>  
 <span data-ttu-id="55c35-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="55c35-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55c35-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55c35-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55c35-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55c35-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55c35-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55c35-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c35-118">参照</span><span class="sxs-lookup"><span data-stu-id="55c35-118">See Also</span></span>  
 [<span data-ttu-id="55c35-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="55c35-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="55c35-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="55c35-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
