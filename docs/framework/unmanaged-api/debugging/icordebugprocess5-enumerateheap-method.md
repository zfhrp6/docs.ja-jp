---
title: ICorDebugProcess5::EnumerateHeap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 412ade32daaed4802215c628ab94b535fc542b93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423346"
---
# <a name="icordebugprocess5enumerateheap-method"></a>ICorDebugProcess5::EnumerateHeap メソッド
マネージ ヒープのオブジェクトの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppObject`  
 [out]アドレスへのポインター、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイスであるオブジェクトをマネージ ヒープ上に存在するオブジェクトの列挙子。  
  
## <a name="remarks"></a>コメント  
 呼び出しの前に、`ICorDebugProcess5::EnumerateHeap`メソッドを呼び出す必要があります、 [icordebugprocess 5::getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)メソッドの値を確認し、 `areGCStructuresValid` 、返されたフィールド[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)現在の状態で、ガベージ コレクション ヒープが列挙可能なことを確認するオブジェクト。 さらに、`ICorDebugProcess5::EnumerateHeap`返します`E_FAIL`マネージ ヒープが割り当てられているが早すぎるのでメモリの前に、プロセスの有効期間にアタッチします。  
  
 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)インターフェイス オブジェクトは、標準的な列挙子を列挙することができます ICorDebugEnum インターフェイスから派生した[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)オブジェクト。 このメソッドは追加、 [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)のコレクション オブジェクト[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)すべてのオブジェクトに関する情報を提供するインスタンス。 コレクションを含めることがありますも[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)でルートがないオブジェクトに関する情報を提供するインスタンスは、オブジェクトが、ガベージ コレクターによって収集されていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
