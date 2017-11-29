---
title: "ICLRDebuggingLibraryProvider インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider
helpviewer_keywords: ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 82ed352e3f5fb83a2f464f2d82ff9a9885227fe7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="50216-102">ICLRDebuggingLibraryProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50216-102">ICLRDebuggingLibraryProvider Interface</span></span>
<span data-ttu-id="50216-103">含まれています、 [ProvideLibrary メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)メソッドで、コールバック インターフェイスの共通言語ランタイム バージョンに固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="50216-103">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50216-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="50216-104">Methods</span></span>  
  
|<span data-ttu-id="50216-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="50216-105">Method</span></span>|<span data-ttu-id="50216-106">説明</span><span class="sxs-lookup"><span data-stu-id="50216-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50216-107">ProvideLibrary メソッド</span><span class="sxs-lookup"><span data-stu-id="50216-107">ProvideLibrary Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="50216-108">により、デバッガーはデバッグ ライブラリの読み込みに使用できるモジュールへのハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="50216-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="50216-109">要件</span><span class="sxs-lookup"><span data-stu-id="50216-109">Requirements</span></span>  
 <span data-ttu-id="50216-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="50216-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50216-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50216-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50216-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50216-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50216-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50216-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50216-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="50216-114">See Also</span></span>  
 [<span data-ttu-id="50216-115">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="50216-115">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="50216-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="50216-116">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
