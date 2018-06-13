---
title: IHostIoCompletionManager::InitializeHostOverlapped メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 023e112aa8273d99efce2e0f2116f95569ac0c3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438969"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped メソッド
ホストは、Win32 に追加するカスタム データを初期化するために営業案件`OVERLAPPED`非同期 I/O 要求に使用される構造です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvOverlapped`  
 [in]Win32 へのポインター `OVERLAPPED` I/O 要求に含まれる構造体。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|E_OUTOFMEMORY|十分なメモリは、要求されたリソースを割り当てることができませんでした。|  
  
## <a name="remarks"></a>コメント  
 Windows プラットフォームの機能を使用して、`OVERLAPPED`非同期 I/O 要求の状態を格納する構造体。 CLR の呼び出し、`InitializeHostOverlapped`ホストのカスタム データを追加する機会を与えるためにメソッド、`OVERLAPPED`インスタンス。  
  
> [!IMPORTANT]
>  得るには、カスタム データ ブロックの先頭に、ホストは、のサイズにオフセットを設定する必要があります、`OVERLAPPED`構造 (`sizeof(OVERLAPPED)`)。  
  
 E_OUTOFMEMORY の戻り値は、そのカスタム データを初期化するために、ホストが失敗したことを示します。 この場合、CLR では、エラーを報告して、呼び出しが失敗します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [GetHostOverlappedSize メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)  
 [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
