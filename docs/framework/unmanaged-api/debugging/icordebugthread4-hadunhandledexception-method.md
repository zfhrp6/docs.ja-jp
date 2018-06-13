---
title: ICorDebugThread4::HadUnhandledException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422111"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException メソッド
スレッドが未処理の例外をしたかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppBlockingObjectEnum`  
 [out]順序付けされた列挙体のアドレスへのポインター [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|スレッドは、未処理の例外の作成後で発生しました。|  
|S_FALSE|スレッドは、未処理の例外にしたことがないです。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、スレッドが未処理の例外をしたかどうかを示します。 時間でハンドルされない例外コールバックをトリガーまたはネイティブの JIT アタッチが開始されると、このメソッドが S_OK を返す保証します。 保証がないこと、 [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)メソッドは、未処理の例外を返します以外のかどうか、プロセスが続行されていないかしたときに、ハンドルされない例外コールバックを取得した後、ただし、ネイティブ JIT アタッチします。 さらに、可能であれば (可能性は低いですが、ネイティブ JIT アタッチがトリガーされた時点で未処理の例外を持つ複数のスレッドにします。 このような場合は、どの例外が JIT アタッチをトリガーを決定する方法はありません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
