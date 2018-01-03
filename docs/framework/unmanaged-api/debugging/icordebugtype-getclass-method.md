---
title: "ICorDebugType::GetClass メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32462159bc00ea766af3e3bc0f9d3d7a35eb2e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass メソッド
インスタンス化されていないジェネリック型を表す ICorDebugClass へのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppClass`  
 [out]アドレスへのポインター、`ICorDebugClass`をインスタンス化されていないジェネリック型を表すインターフェイス。  
  
## <a name="remarks"></a>コメント  
 `GetClass`特定の条件下でのみ呼び出すことができます。 呼び出す[icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)呼び出す前に`GetClass`です。 場合`ICorDebugType::GetType`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE、CorElementType 値を返します`GetClass`を呼び出すと、ジェネリック型のインスタンス化されていない型を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
