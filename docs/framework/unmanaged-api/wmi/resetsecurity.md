---
title: "ResetSecurity 関数 (アンマネージ API リファレンス)"
description: "ResetSecurity 関数では、現在のスレッドに偽装トークンを割り当てます。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bacee65633d25e705d978d3902a6804516a88bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resetsecurity-function"></a>ResetSecurity 関数
指定された権限借用トークンを現在のスレッドに割り当てます。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>パラメーター

`token`  
[in]現在のスレッドに関連付ける権限借用トークンです。 この値は `null` の場合もあります。 

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は`S_OK`(0) です。

関数が失敗した場合、戻り値がゼロ以外のエラー コードです。 拡張エラー情報を取得する呼び出し、 [GetErrorInfo](geterrorinfo.md)関数。
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
