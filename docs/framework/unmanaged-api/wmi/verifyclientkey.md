---
title: "VerifyClientKey 関数 (アンマネージ API リファレンス)"
description: "VerifyClientKey 関数により、クライアント キーが正しいセキュリティ。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cce10e3dd5536a85b4dee62cc7f6e9e8e73929cb
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="9fc72-103">VerifyClientKey 関数</span><span class="sxs-lookup"><span data-stu-id="9fc72-103">VerifyClientKey function</span></span>
<span data-ttu-id="9fc72-104">により、クライアント キーは、適切なセキュリティ。</span><span class="sxs-lookup"><span data-stu-id="9fc72-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9fc72-105">構文</span><span class="sxs-lookup"><span data-stu-id="9fc72-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="9fc72-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="9fc72-106">Return value</span></span>

<span data-ttu-id="9fc72-107">関数が成功した場合、戻り値は`ERROR_SUCCESS`(0) です。</span><span class="sxs-lookup"><span data-stu-id="9fc72-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="9fc72-108">戻り値で定義されている 0 以外のエラー コードは、関数が失敗した場合、 *WinError.h*です。</span><span class="sxs-lookup"><span data-stu-id="9fc72-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="9fc72-109">要件</span><span class="sxs-lookup"><span data-stu-id="9fc72-109">Requirements</span></span>  
 <span data-ttu-id="9fc72-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9fc72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fc72-111">**ヘッダー:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="9fc72-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="9fc72-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9fc72-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fc72-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fc72-113">See also</span></span>  
[<span data-ttu-id="9fc72-114">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9fc72-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
