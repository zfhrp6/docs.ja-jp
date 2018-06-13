---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc900ca20ac87ddecfd8f7adf0894af21ca5d2f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418091"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity メソッド
コードの実行が編集された関数の古いバージョンのシーケンス ポイントに達したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]編集済みの関数を含む、アプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]リマップ ブレークポイントが発生しました、スレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pOldFunction`  
 [in]現在のスレッドで実行されている関数のバージョンを表す ICorDebugFunction オブジェクトへのポインター。  
  
 `pNewFunction`  
 [in]関数の最新バージョンを表す ICorDebugFunction オブジェクトへのポインター。  
  
 `oldILOffset`  
 [in]命令ポインターの古いバージョンの関数での Microsoft intermediate language (MSIL) オフセットします。  
  
## <a name="remarks"></a>コメント  
 このコールバックは、デバッガーを呼び出すことによって、新しいバージョンの指定された関数内の正しい場所への命令ポインターを再マップする機会を与える、 [icordebugilframe 2::remapfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)メソッドです。 場合は、デバッガーを呼び出しません`RemapFunction`呼び出す前に、 [icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)メソッド、ランタイムの古いコードの実行を続行し、別が起動されます`FunctionRemapOpportunity`次のシーケンス ポイントでのコールバック。  
  
 デバッガーが S_OK を返すまで、指定された関数の古いバージョンを実行しているすべてのフレームには、このコールバックが呼び出されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
