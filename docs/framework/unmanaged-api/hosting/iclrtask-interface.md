---
title: ICLRTask インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ba53e4af114773a347d15b7308dc4c3567154e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435707"
---
# <a name="iclrtask-interface"></a>ICLRTask インターフェイス
ホストまたは関連付けられているタスクは、CLR に通知を提供する共通言語ランタイム (CLR) の要求を行うことができるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR がタスクを中止する要求を現在`ICLRTask`インスタンスが表すです。|  
|[ExitTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|タスクに現在関連付けられている、CLR に通知`ICLRTask`インスタンスが終了し、タスクを正常にシャット ダウンしようとしています。|  
|[GetMemStats メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|現在のタスクでメモリ リソースの使用に関する統計情報を取得`ICLRTask`インスタンス。|  
|[LocksHeld メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|タスクで現在保持されているロックの数を取得します。|  
|[NeedsPriorityScheduling メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|ホストが現在によって表されるタスクの再スケジュールする高優先順位を割り当てる必要があるかどうかを示す値を取得`ICLRTask`インスタンス。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|ホストが、タスクが完了し、現在を再利用する CLR を有効にことを CLR に通知`ICLRTask`を別のタスクを表すインスタンス。|  
|[RudeAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Clr は現在のタスクを中止する`ICLRTask`ファイナライザーが実行されるを待機せず、すぐにインスタンス化します。|  
|[SetTaskIdentifier メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|現在のタスクの一意の識別子を設定`ICLRTask`デバッグで使用するためのインスタンス。|  
|[SwitchIn メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|現在のタスクが表す CLR に通知`ICLRTask`インスタンスが操作可能な状態にします。|  
|[SwitchOut メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|現在のタスクが表す CLR に通知`ICLRTask`インスタンスは操作可能な状態ではありません。|  
|[YieldTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|CLR make の他のタスクで使用できるプロセッサ時間を要求します。 CLR は、タスクが処理時間を得ることのできる状態になるという保証を行いません。|  
  
## <a name="remarks"></a>コメント  
 `ICLRTask` CLR のタスクの表現です。 、任意の時点でコードが実行中には、タスクを実行するいると、実行を待機しているどちらかに記述できます。 ホストの呼び出し、 `ICLRTask::SwitchIn` CLR に通知するメソッドをタスクを現在`ICLRTask`インスタンスを表すは操作可能な状態にします。 呼び出しの後に`ICLRTask::SwitchIn`、ホストは、ランタイムへの呼び出しで指定されたスレッド アフィニティが必要な場合を除く任意のオペレーティング システム スレッドでタスクをスケジュールすることができます、 [ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)と[Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)メソッドです。 しばらくしてから、オペレーティング システムは、スレッドからタスクを削除し、実行されていない状態に配置することができます。 たとえば、タスクの同期プリミティブをブロックまたは I/O 操作の完了を待機するたびに発生するこのです。 ホスト呼び出し[SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)が現在のタスクが表す CLR に通知`ICLRTask`インスタンスは操作可能な状態ではありません。  
  
 タスクは、通常、コードの実行の最後に終了します。 ホストを呼び出して、その時点で`ICLRTask::ExitTask`、関連付けられているを破棄する`ICLRTask`です。 ただし、タスクできますもリサイクルへの呼び出しを使用して、 `ICLRTask::Reset`、これにより、`ICLRTask`再使用するインスタンス。 このアプローチには、繰り返しの作成とインスタンスを破棄のオーバーヘッドができないようにします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
