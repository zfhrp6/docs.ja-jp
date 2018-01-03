---
title: "ICorDebugProcess5::EnumerateHandles メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9bf9f1a4d565e0af4f3ee34a2805116407027d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles メソッド
プロセスで、オブジェクト ハンドルの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `types`  
 [in]ビットごとの組み合わせ[CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)コレクションに含めるへのハンドルの種類を指定します。  
  
 `ppENum`  
 [out]アドレスへのポインター、 [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)つまりする列挙子オブジェクトのガベージ コレクションします。  
  
## <a name="remarks"></a>コメント  
 `EnumerateHandles`ハンドル テーブルの検査をサポートするヘルパー関数です。 に似ていますが、 [icordebugprocess 5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)点を除いて、メソッドを設定するのではなく、 [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)ガベージ コレクション、すべてのオブジェクトを使用して、コレクション、ハンドル テーブルからハンドルを持つオブジェクトだけが含まれます。  
  
 `types`パラメーターがコレクションに含めるハンドルの種類を指定します。 `types`次の 3 つのメンバーのいずれかを指定できます、 [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)列挙します。  
  
-   `CorHandleStrongOnly`(ハンドルを厳密な参照のみ)。  
  
-   `CorHandleWeakOnly`(弱参照のみを処理)。  
  
-   `CorHandleAll`(すべてのハンドル)。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
