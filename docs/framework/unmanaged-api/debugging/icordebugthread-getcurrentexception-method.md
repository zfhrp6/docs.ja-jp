---
title: ICorDebugThread::GetCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82686fdd14783257987ec5bf9a24db7d87049d42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421747"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException メソッド
マネージ コードによってスローされる例外を表す ICorDebugValue オブジェクトへのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppExceptionObject`  
 [out]アドレスへのポインター、`ICorDebugValue`マネージ コードをによってスローされる例外を表すオブジェクト。  
  
## <a name="remarks"></a>コメント  
 例外オブジェクトが終了するまで、例外がスローされたときから存在、`catch`ブロックします。 ICorDebugEval メソッドによって実行される、関数の評価はセットアップの例外オブジェクトをクリアし、完了時に復元します。  
  
 例外は、(たとえば、フィルターまたは関数の評価で、例外がスローされた) 場合、入れ子にでき、シングル スレッド内で複数の未処理の例外が発生する可能性があります。 `GetCurrentException` 最新の例外を返します。  
  
 例外オブジェクトと型については、例外の有効期間全体で変更できます。 たとえば、x の種類の例外がスローされた後に、共通言語ランタイム (CLR) 可能性がありますメモリが不足し、メモリ不足の例外に昇格させることです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
