---
title: "VerifyClientKey 関数 (アンマネージ API リファレンス)"
description: "VerifyClientKey 関数により、クライアント キーが正しいセキュリティ。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ada878ff8bc430ab2a2d48cac13a81b1f64d39f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="48e34-103">VerifyClientKey 関数</span><span class="sxs-lookup"><span data-stu-id="48e34-103">VerifyClientKey function</span></span>
<span data-ttu-id="48e34-104">により、クライアント キーは、適切なセキュリティ。</span><span class="sxs-lookup"><span data-stu-id="48e34-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="48e34-105">構文</span><span class="sxs-lookup"><span data-stu-id="48e34-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="48e34-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="48e34-106">Return value</span></span>

<span data-ttu-id="48e34-107">関数が成功した場合、戻り値は`ERROR_SUCCESS`(0) です。</span><span class="sxs-lookup"><span data-stu-id="48e34-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="48e34-108">戻り値で定義されている 0 以外のエラー コードは、関数が失敗した場合、 *WinError.h*です。</span><span class="sxs-lookup"><span data-stu-id="48e34-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="48e34-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="48e34-109">Requirements</span></span>  
 <span data-ttu-id="48e34-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48e34-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e34-111">**ヘッダー:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="48e34-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="48e34-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="48e34-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e34-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="48e34-113">See also</span></span>  
[<span data-ttu-id="48e34-114">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="48e34-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
