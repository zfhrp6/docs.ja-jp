---
title: "Initialize 関数 (アンマネージ API リファレンス)"
description: "初期化関数は、WMI の初期化を実行します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Initialize
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Initialize
helpviewer_keywords: Initialize function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ed0e0127608f9f80a2661067dd9a6025fd579a7
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="initialize-function"></a>Initialize 関数
WMI の初期化を実行します。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a>パラメーター

`bAllowIManagementObjectQI`   
[in]`true` WMI オブジェクトでの queryinterface 呼び出しが許可されるを示すために`false`それ以外の場合。

## <a name="return-value"></a>戻り値

関数は常に返します`S_OK`(0) です。
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** WMINet_Utils.def  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
