---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ba09991e9452a86c6b7a1cbb08a38a71ba2aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416765"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド
このオブジェクトのモニター ロックを所有するマネージ スレッドを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppThread`  
 [out]このオブジェクトのモニター ロックを所有するマネージ スレッドです。  
  
 `pAcquisitionCount`  
 [out]このスレッドが所有されていない中に返す前に、ロックを解除する必要があります回数。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|S_FALSE|このオブジェクトのモニター ロックを所有するマネージ スレッドがありません。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 マネージ スレッドは、このオブジェクトのモニター ロックを所有している: 場合  
  
-   このメソッドは、S_OK を返します。  
  
-   スレッド オブジェクトは、スレッドが終了するまで有効です。  
  
 マネージ スレッドに、このオブジェクトのモニター ロックを所有していない場合`ppThread`と`pAcquisitionCount`は変更されず、S_FALSE が返されます。  
  
 場合`ppThread`または`pAcquisitionCount`は有効なポインターではありません、結果は未定義です。  
  
 スレッドがこのオブジェクトのモニター ロックを所有している場合、これを確認できないように、エラーが発生した場合、メソッドは失敗を示す HRESULT を返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
