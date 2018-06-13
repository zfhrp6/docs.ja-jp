---
title: VerifyClientKey 関数 (アンマネージ API リファレンス)
description: VerifyClientKey 関数により、クライアント キーが正しいセキュリティ。
ms.date: 11/06/2017
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
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459565"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey 関数
により、クライアント キーは、適切なセキュリティ。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は`ERROR_SUCCESS`(0) です。

戻り値で定義されている 0 以外のエラー コードは、関数が失敗した場合、 *WinError.h*です。

## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.def  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
