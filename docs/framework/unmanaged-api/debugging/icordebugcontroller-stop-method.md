---
title: ICorDebugController::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cd0fc9f86515d63533275002301eb47f11feebb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411267"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop メソッド
プロセスでマネージ コードを実行しているすべてのスレッドを協調停止を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwTimeoutIgnored`  
 使用しません。  
  
## <a name="remarks"></a>コメント  
 `Stop` プロセスの管理を実行しているすべてのスレッドでの協調停止コードを実行します。 マネージのみのデバッグ セッション中にアンマネージ スレッドは実行を続行 (ただし、マネージ コードを呼び出すしようとするときはブロックされます)。 相互運用機能デバッグ セッション中には、アンマネージ スレッドも停止されます。 `dwTimeoutIgnored`現在値が無視され、無限 (-1) として扱われます。 協調停止は、デッドロックのため失敗すると、すべてのスレッドは中断され、E_TIMEOUT が返されます。  
  
> [!NOTE]
>  `Stop` デバッグ API でのみ同期メソッドです。 ときに`Stop`場合は s_ok、プロセスが停止します。 リスナーに、停止の通知コールバックは与えられません。 デバッガーを呼び出す必要があります[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)を再開するプロセスが可能にします。  
  
 デバッガーは、停止カウンターを保持します。 カウンターがゼロになる、コント ローラーが再開されます。 各呼び出し`Stop`または各ディスパッチされたコールバックがカウンターをインクリメントします。 各呼び出し`ICorDebugController::Continue`デクリメント カウンターです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
