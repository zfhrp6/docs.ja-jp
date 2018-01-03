---
title: "ICorDebugFunction::GetCurrentVersionNumber メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetCurrentVersionNumber
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c230c8ca6da69b45d05b3319220eacfa6c1f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a>ICorDebugFunction::GetCurrentVersionNumber メソッド
この ICorDebugFunction オブジェクトによって表される関数に対して行われた最後の編集のバージョン番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pnCurrentVersion`  
 [out]この関数に対する最後の編集のバージョンの数を表す整数値へのポインター。  
  
## <a name="remarks"></a>コメント  
 この関数に対する最後の編集のバージョン番号は、関数自体のバージョン番号より大きい可能性があります。 いずれかを使用して、 [icordebugfunction 2::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md)メソッドまたは[icordebugcode::getversionnumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)関数のバージョン番号を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
