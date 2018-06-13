---
title: IHostSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa9f039cb7eaa7ccd22bad36098c00a697d818d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443974"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager インターフェイス
共通言語ランタイム (CLR) に、Win32 の同期の関数を使用する代わりに、ホストを呼び出すことによって同期プリミティブを作成できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateAutoEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|自動リセット イベント オブジェクトを作成します。|  
|[CreateCrst メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|同期のためのクリティカル セクション オブジェクトを作成します。|  
|[CreateCrstWithSpinCount メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|同期用のスピン カウントをクリティカル セクション オブジェクトを作成します。|  
|[CreateManualEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|手動リセット イベント オブジェクトを作成します。|  
|[CreateMonitorEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|監視対象の自動リセット イベント オブジェクトを作成します。|  
|[CreateRWLockReaderEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|リーダー ロックを実装するための手動リセット イベント オブジェクトを作成します。|  
|[CreateRWLockWriterEvent メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|ライター ロックの実装の自動リセット イベント オブジェクトを作成します。|  
|[CreateSemaphore メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|作成、 [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)待機イベントのセマフォとして使用する CLR のオブジェクト。|  
|[SetCLRSyncManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|セット、 [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)に現在関連付けインスタンス`IHostSyncManager`インスタンス。|  
  
## <a name="remarks"></a>コメント  
 CLR のホストの実装を検出する`IHostSyncManager`を呼び出して、 [ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)メソッドを`IID`IID_IHostSyncManager のです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
