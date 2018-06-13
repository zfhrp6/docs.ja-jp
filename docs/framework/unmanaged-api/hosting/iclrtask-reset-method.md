---
title: ICLRTask::Reset メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29267d032f5e38e352592edc50dbded68aaa9f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435943"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset メソッド
共通言語ランタイム (CLR) を通知ホストが完了するタスクと、現在の再利用する CLR を有効に[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)を別のタスクを表すインスタンス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fFull`  
 [in]`true`場合は、ランタイムは、現在に関連するセキュリティおよびロケールの情報に加え、スレッド関連の静的な値をリセットする必要があります、`ICLRTask`インスタンス。 それ以外の場合、`false`です。  
  
 値が場合`true`、ランタイムを使用して格納されたデータをリセットする<xref:System.Threading.Thread.AllocateDataSlot%2A>または<xref:System.Threading.Thread.AllocateNamedDataSlot%2A>です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Reset` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しを実行します。 正常に|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 CLR は、以前に作成されたリサイクルできる`ICLRTask`インスタンスに新しいタスクが必要があるたびに、新しいインスタンスを繰り返し作成のオーバーヘッドを回避します。 ホストでは、この機能を有効を呼び出して`ICLRTask::Reset`の代わりに[iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)タスクを完了したとき。 次の一覧は、通常のライフ サイクルをまとめたもの、`ICLRTask`インスタンス。  
  
1.  ランタイムが新たに作成`ICLRTask`インスタンス。  
  
2.  ランタイム呼び出し[ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)を現在のタスクにホストへの参照を取得します。  
  
3.  ランタイム呼び出し[ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)タスクに関連付ける新しいインスタンスのホストです。  
  
4.  タスクを実行し、完了します。  
  
5.  ホストを呼び出すことによって、タスクを破棄`ICLRTask::ExitTask`です。  
  
 `Reset` このシナリオでは、2 つの方法を変更します。 手順 5. 上でホストの呼び出しで`Reset`タスクをクリーンな状態にリセットする、分離と、`ICLRTask`からそれに関連付けられたインスタンス[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)インスタンス。 ホストをキャッシュできますも、必要な場合、`IHostTask`インスタンスを再利用します。 手順 1 上で、ランタイムは、リサイクルをプル`ICLRTask`新しいインスタンスを作成する代わりにキャッシュからします。  
  
 この方法は、ホストにも再利用可能なワーカー タスクのプールがある場合に機能します。 ときに、ホストのいずれかの`IHostTask`インスタンス、対応するが破棄されます`ICLRTask`を呼び出して`ExitTask`です。  
  
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
