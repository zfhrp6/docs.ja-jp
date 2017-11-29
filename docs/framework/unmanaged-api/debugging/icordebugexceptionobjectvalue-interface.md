---
title: "ICorDebugExceptionObjectValue インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 47733a6af18d42d0d9db1e50cf21646289ef1443
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="8636d-102">ICorDebugExceptionObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8636d-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="8636d-103">マネージ例外オブジェクトからスタック トレース情報を提供する"ICorDebugObjectValue"インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="8636d-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8636d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8636d-104">Methods</span></span>  
  
|<span data-ttu-id="8636d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8636d-105">Method</span></span>|<span data-ttu-id="8636d-106">説明</span><span class="sxs-lookup"><span data-stu-id="8636d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8636d-107">EnumerateExceptionCallStack メソッド</span><span class="sxs-lookup"><span data-stu-id="8636d-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="8636d-108">例外オブジェクトに埋め込まれているコール スタックには、列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="8636d-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8636d-109">コメント</span><span class="sxs-lookup"><span data-stu-id="8636d-109">Remarks</span></span>  
 <span data-ttu-id="8636d-110">呼び出し`QueryInterface`はから派生するマネージ オブジェクトの成功<xref:System.Exception?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="8636d-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8636d-111">要件</span><span class="sxs-lookup"><span data-stu-id="8636d-111">Requirements</span></span>  
 <span data-ttu-id="8636d-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8636d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8636d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8636d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8636d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8636d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8636d-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8636d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8636d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8636d-116">See Also</span></span>  
 [<span data-ttu-id="8636d-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8636d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8636d-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8636d-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
