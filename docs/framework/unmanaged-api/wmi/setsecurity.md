---
title: "SetSecurity 関数 (アンマネージ API リファレンス)"
description: "SetSecurity 関数では、現在のスレッドの偽装トークンを取得します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: SetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: SetSecurity
helpviewer_keywords: SetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb716d64bde9b298203e54d862ff4f1b2bcd170
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setsecurity-function"></a>SetSecurity 関数
現在のスレッドに関連付けられている権限借用トークンを取得します。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```  

## <a name="parameters"></a>パラメーター

`pNeedToReset`[out]ポインターを含む、関数から制御が戻るとき、`boolean`を呼び出してトークンをリセットするかどうかを示す、 [ResetSecurity](resetsecurity.md)関数。  

`token`  
[out]関数から制御が戻るときに、現在のスレッドに関連付けられている権限借用トークンのハンドルへのポインターが含まれています。 その値を指定できます`null`かどうかは、現在のスレッドに関連付けられているトークンはありません。 

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は`S_OK`(0) です。

関数が失敗した場合、戻り値がゼロ以外のエラー コードです。 拡張エラー情報を取得する呼び出し、 [GetErrorInfo](geterrorinfo.md)関数。
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
