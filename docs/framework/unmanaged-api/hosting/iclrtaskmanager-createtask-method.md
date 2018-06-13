---
title: ICLRTaskManager::CreateTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f731e121324793a027c5977a02e1973b0d6fff20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439649"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask メソッド
共通言語ランタイム (CLR) が新しいタスクを作成することを明示的に要求します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pTask`  
 [out]新しく作成されたのアドレスへのポインター [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)、または null の場合は、タスクを作成できませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|E_OUTOFMEMORY|十分なメモリが要求されたリソースを割り当てることができます。|  
  
## <a name="remarks"></a>コメント  
 ユーザー コード内の型を使用してスレッドを作成するときに、CLR が初期化時に自動的に新しいタスクを作成、<xref:System.Threading>名前空間、スレッド プールのサイズを増加する場合またはします。 また、アンマネージ コードがマネージ関数の呼び出しを行うときにも、タスクを作成します。  
  
 `CreateTask` CLR が新しいタスクを作成する明示的な要求をホストできるようにします。 たとえば、ホストは、データ構造を事前初期設定するには、このメソッドを呼び出すことができます。  
  
> [!IMPORTANT]
>  新しいタスクが中断状態が返され、ホストを明示的に呼び出すまで、中断されたまま[ihosttask::start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
