---
title: ICorDebugExceptionObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6805b7b49f76b80161aef5051fe3c284192f582
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413775"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="561d3-102">ICorDebugExceptionObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="561d3-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="561d3-103">マネージ例外オブジェクトからスタック トレース情報を提供する"ICorDebugObjectValue"インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="561d3-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="561d3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="561d3-104">Methods</span></span>  
  
|<span data-ttu-id="561d3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="561d3-105">Method</span></span>|<span data-ttu-id="561d3-106">説明</span><span class="sxs-lookup"><span data-stu-id="561d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="561d3-107">EnumerateExceptionCallStack メソッド</span><span class="sxs-lookup"><span data-stu-id="561d3-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="561d3-108">例外オブジェクトに埋め込まれているコール スタックには、列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="561d3-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="561d3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="561d3-109">Remarks</span></span>  
 <span data-ttu-id="561d3-110">呼び出し`QueryInterface`はから派生するマネージ オブジェクトの成功<xref:System.Exception?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="561d3-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="561d3-111">要件</span><span class="sxs-lookup"><span data-stu-id="561d3-111">Requirements</span></span>  
 <span data-ttu-id="561d3-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="561d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="561d3-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="561d3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="561d3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="561d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="561d3-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="561d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="561d3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="561d3-116">See Also</span></span>  
 [<span data-ttu-id="561d3-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="561d3-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="561d3-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="561d3-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
