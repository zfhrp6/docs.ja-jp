---
title: "ICorDebugThread::GetDebugState メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetDebugState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b9d310cdc088e4b2fc9c6850accc3576a6147ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState メソッド
ICorDebugThread オブジェクトの現在のデバッグ状態を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pState`  
 [out]このスレッドの現在のデバッグ状態を説明する CorDebugThreadState 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>コメント  
 プロセスが現在停止している場合`pState`プロセス続行するか、このスレッドの実際の現在状態にない場合は、このスレッドに対して存在デバッグ状態を表します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
