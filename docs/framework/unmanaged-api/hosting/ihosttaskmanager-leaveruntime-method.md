---
title: IHostTaskManager::LeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444478"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime メソッド
現在実行中のタスクが共通言語ランタイム (CLR) のままにし、アンマネージ コードの入力があるホストに通知します。  
  
> [!IMPORTANT]
>  対応する呼び出し[ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)現在実行中のタスクがマネージ コードを再入力するホストに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `target`  
 [in]アンマネージ関数を呼び出すのマップされたポータブル実行可能ファイル内のアドレス。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|E_OUTOFMEMORY|十分なメモリがある要求の割り当てを完了します。|  
  
## <a name="remarks"></a>コメント  
 アンマネージ コードとの間の呼び出しシーケンスは、入れ子にすることができます。 たとえば、次の表に仮想的な状況への呼び出しのシーケンス`LeaveRuntime`、 [ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)、 [ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)、および`IHostTaskManager::EnterRuntime`ホストが入れ子になったレイヤーを特定できるようにします。  
  
|アクション|対応するメソッドの呼び出し|  
|------------|-------------------------------|  
|マネージ Visual Basic 実行可能なプラットフォームを使用して、C で記述されたアンマネージ関数を呼び出します。|`IHostTaskManager::LeaveRuntime`|  
|アンマネージ C 関数は、c# で記述されたマネージ DLL でメソッドを呼び出します。|`IHostTaskManager::ReverseEnterRuntime`|  
|C# の場合、マネージ関数が C で記述された別のアンマネージ関数を呼び出してもプラットフォーム呼び出しを使用します。|`IHostTaskManager::LeaveRuntime`|  
|2 番目のアンマネージ関数では、c# 関数への実行を返します。|`IHostTaskManager::EnterRuntime`|  
|C# 関数は、最初のアンマネージ関数に実行を返します。|`IHostTaskManager::ReverseLeaveRuntime`|  
|1 つ目のアンマネージ関数では、Visual Basic プログラムに実行を返します。|`IHostTaskManager::EnterRuntime`|  
  
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
