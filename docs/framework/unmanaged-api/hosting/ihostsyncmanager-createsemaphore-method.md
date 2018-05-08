---
title: IHostSyncManager::CreateSemaphore メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 003e385ade6357b76823986d20e8fdf3d4c3757f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a>IHostSyncManager::CreateSemaphore メソッド
作成、 [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)待機イベントのセマフォとして使用する共通言語ランタイム (CLR) のオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwInitial`  
 [in]初期カウント`ppSemaphore`です。  
  
 `dwMax`  
 [in]最大カウント`ppSemaphore`です。  
  
 `ppSemaphore`  
 [out]アドレスへのポインター、`IHostSemaphore`インスタンス、または null の場合、セマフォを作成できませんでした。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`CreateSemaphore` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|E_OUTOFMEMORY|十分なメモリは、要求されたイベント オブジェクトを作成できませんでした。|  
  
## <a name="remarks"></a>コメント  
 `CreateSemaphore` 同じ名前を持つ Win32 関数を反映します。 `dwInitial`と`dwMax`パラメーターは、セマフォのカウントの同じセマンティクスを使用して、Win32 として`lInitialCount`と`lMaximumCount`パラメーター、それぞれします。 `dwInitial` 0 以上にする必要がありますと`dwMax`、包括的です。 `dwMax` 0 より大きくなければなりません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSemaphore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
