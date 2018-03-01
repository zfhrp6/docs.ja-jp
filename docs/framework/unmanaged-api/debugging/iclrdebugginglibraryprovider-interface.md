---
title: "ICLRDebuggingLibraryProvider インターフェイス"
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
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7320bf261f28fed85c44f2550df5ecd06421290
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="9bf73-102">ICLRDebuggingLibraryProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9bf73-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="9bf73-103">含まれています、 [ProvideLibrary メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)メソッドで、コールバック インターフェイスの共通言語ランタイム バージョンに固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="9bf73-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bf73-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9bf73-104">Methods</span></span>  
  
|<span data-ttu-id="9bf73-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9bf73-105">Method</span></span>|<span data-ttu-id="9bf73-106">説明</span><span class="sxs-lookup"><span data-stu-id="9bf73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9bf73-107">ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="9bf73-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="9bf73-108">により、デバッガーはデバッグ ライブラリの読み込みに使用できるモジュールへのハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="9bf73-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9bf73-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="9bf73-109">Requirements</span></span>  
 <span data-ttu-id="9bf73-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bf73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf73-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bf73-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bf73-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bf73-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bf73-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf73-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf73-114">参照</span><span class="sxs-lookup"><span data-stu-id="9bf73-114">See Also</span></span>  
 [<span data-ttu-id="9bf73-115">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9bf73-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9bf73-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="9bf73-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
