---
title: "ICLRDebugging インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging
helpviewer_keywords: ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3e061b95faafeec3c3d233ab54f128a23c3264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="1dcef-102">ICLRDebugging インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dcef-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="1dcef-103">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1dcef-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dcef-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1dcef-104">Methods</span></span>  
  
|<span data-ttu-id="1dcef-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1dcef-105">Method</span></span>|<span data-ttu-id="1dcef-106">説明</span><span class="sxs-lookup"><span data-stu-id="1dcef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dcef-107">OpenVirtualProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="1dcef-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="1dcef-108">プロセスに読み込まれている共通言語ランタイム (CLR) モジュールに対応する"ICorDebugProcess"インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="1dcef-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="1dcef-109">CanUnloadNow メソッド</span><span class="sxs-lookup"><span data-stu-id="1dcef-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="1dcef-110">ライブラリで提供されているかどうかを判断、 [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)インターフェイスが使用されているまたは読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="1dcef-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dcef-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1dcef-111">Remarks</span></span>  
 <span data-ttu-id="1dcef-112">インスタンスを取得することができます、`ICLRDebugging`インターフェイスを使用して、 [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="1dcef-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dcef-113">要件</span><span class="sxs-lookup"><span data-stu-id="1dcef-113">Requirements</span></span>  
 <span data-ttu-id="1dcef-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1dcef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcef-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1dcef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dcef-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dcef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dcef-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcef-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dcef-118">See Also</span></span>  
 [<span data-ttu-id="1dcef-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dcef-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1dcef-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="1dcef-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
