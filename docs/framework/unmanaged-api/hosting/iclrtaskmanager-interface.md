---
title: ICLRTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14c2c9b70ac2e57983ea4b16772add6a1dff5ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438068"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager インターフェイス
共通言語ランタイム (CLR) を明示的に要求するホストに許可するメソッドが新しいタスクを作成し、現在実行中のタスクを取得および地理的な言語およびタスクのカルチャを設定を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|CLR を作成する新しいことを明示的に要求[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インスタンス。|  
|[GetCurrentTask メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|取得、`ICLRTask`を現在実行中のタスクを表すインスタンス。|  
|[GetCurrentTaskType メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|現在実行中のタスクの種類を取得します。|  
|[SetLocale メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|ホストが現在実行中のタスクのロケール識別子を変更したことを CLR に通知します。|  
|[SetUILocale メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|ホストが現在実行中のタスクのユーザー インターフェイスのロケール識別子を変更したことを共通言語ランタイムに通知します。|  
  
## <a name="remarks"></a>コメント  
 ホストされた環境で実行されている各タスクは、ホスト側の両方の表現を持って (のインスタンス[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) と CLR の側 (のインスタンス[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md))。 ホストまたは CLR のいずれかが、タスクの作成を開始できますが、ホスト側の表現は、ホストとタスクに関する CLR の間の通信を成功させるのに対応する CLR 側表現を関連付ける必要があります。 2 つのオブジェクトは作成され、オペレーティング システムのスレッドで実行するマネージ コードにインスタンス化する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
