---
title: GetErrorInfo 関数 (アンマネージ API リファレンス)
description: GetErrorInfo 関数は、前の関数呼び出しからエラー情報を取得します。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef52a4e503597e08eae407571f02bf63adafc4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455959"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="80bab-103">GetErrorInfo 関数</span><span class="sxs-lookup"><span data-stu-id="80bab-103">GetErrorInfo function</span></span>
<span data-ttu-id="80bab-104">前の関数呼び出しからエラー情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="80bab-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="80bab-105">構文</span><span class="sxs-lookup"><span data-stu-id="80bab-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="80bab-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="80bab-106">Return value</span></span>

<span data-ttu-id="80bab-107">ポインター、 [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx)関数呼び出しが成功した場合は、オブジェクトまたは`null`が失敗した場合。</span><span class="sxs-lookup"><span data-stu-id="80bab-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="80bab-108">コメント</span><span class="sxs-lookup"><span data-stu-id="80bab-108">Remarks</span></span>

<span data-ttu-id="80bab-109">この関数への呼び出しをラップする、 [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="80bab-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80bab-110">要件</span><span class="sxs-lookup"><span data-stu-id="80bab-110">Requirements</span></span>  
 <span data-ttu-id="80bab-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="80bab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80bab-112">**ヘッダー:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="80bab-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="80bab-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="80bab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80bab-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="80bab-114">See also</span></span>  
[<span data-ttu-id="80bab-115">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="80bab-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
