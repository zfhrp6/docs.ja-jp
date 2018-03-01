---
title: "ICorDebugChain::GetCallee メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee メソッド
このチェーンによって呼び出されたチェーンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppChain`  
 [out]呼び出されたチェーンを表す ICorDebugChain オブジェクトのアドレスへのポインター。 場合 (つまり、このチェーンを返すと呼ばれるチェーンが待機していない) 場合、このチェーンが現在実行中、`ppChain`は null になります。  
  
## <a name="remarks"></a>コメント  
 このチェーンと呼ばれるチェーンの実行を再開する前に戻るには待機します。 スレッド間のマーシャ リングされた呼び出しの場合、別のスレッドで呼び出されたチェーンがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
