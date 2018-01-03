---
title: "ICorDebugVariableHome::GetLocationType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec44705f75959dce893932789b026504d65a3105
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetlocationtype-method"></a>ICorDebugVariableHome::GetLocationType メソッド
変数のネイティブの場所の種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pLocationType`  
 [out]変数のネイティブの場所の種類へのポインター。  参照してください、 [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)詳細情報を列挙します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [VariableLocationType 列挙型](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
