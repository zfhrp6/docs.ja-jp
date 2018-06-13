---
title: IHostTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9715738931d1b6a91ad9fae7e00ba607905d380f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449065"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager インターフェイス
共通言語ランタイム (CLR)、標準のオペレーティング システムのスレッドやファイバーの関数を使用する代わりに、ホストでタスクを処理できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginDelayAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|現在のタスクを中止できません期間が入るマネージ コードをホストに通知します。|  
|[BeginThreadAffinity メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|マネージ コードをホストが、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を入力することを通知します。|  
|[CallNeedsHostHook メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|共通言語ランタイムがアンマネージ関数に指定された呼び出しをインライン展開をできるかどうかを指定するホストを有効にします。|  
|[CreateTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|要求のホストが新しいタスクを作成することです。|  
|[EndDelayAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|マネージ コードをホストが終了するに通知を現在のタスクを中断できない、期間、事前に呼び出した`BeginDelayAbort`です。|  
|[EndThreadAffinity メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|マネージ コードをホストが終了する、現在のタスクを別のオペレーティング システム スレッドに移動できない期間を以前の呼び出しに通知`BeginThreadAffinity`です。|  
|[EnterRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|アンマネージ メソッドを呼び出し、プラットフォーム呼び出しメソッドなどに返すこと実行の制御、CLR をホストに通知します。|  
|[GetCurrentTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|この呼び出しが行われる元のオペレーティング システムのスレッドで現在実行中のタスクへのインターフェイス ポインターを取得します。|  
|[GetStackGuarantee メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|プロセスの終了前に、スタック操作の完了後に、使用することが保証されるスタック領域の量を取得します。|  
|[LeaveRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|アンマネージ関数呼び出しを行うには、マネージ コードをホストに通知します。|  
|[ReverseEnterRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|呼び出しがアンマネージ コードから共通言語ランタイム (CLR) に作成されていることをホストに通知します。|  
|[ReverseLeaveRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|コントロールが、CLR のままであり、さらに、マネージ コードから呼び出されたアンマネージ関数を入力することをホストに通知します。|  
|[SetCLRTaskManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|により、ホストへのインターフェイス ポインターで、 [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)インスタンスの CLR によって実装されます。|  
|[SetLocale メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|CLR の現在のタスクのロケールが変更されたことをホストに通知します。|  
|[SetStackGuarantee メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|内部使用専用に予約されています。|  
|[SetUILocale メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|現在のタスクのユーザー インターフェイスのロケールが変更されたことをホストに通知します。|  
|[Sleep メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|現在のタスクがスリープ状態にしようとしていることをホストに通知します。|  
|[SwitchToTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|現在のタスクを切り離すことをホストに通知します。|  
  
## <a name="remarks"></a>コメント  
 `IHostTaskManager` CLR タスクを作成および管理には、マネージとアンマネージ コードは逆から制御が転送されるときにアクションを実行し、特定のアクションを指定するためのフックを提供するホストことができます、コードの実行中に取ることはできません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
