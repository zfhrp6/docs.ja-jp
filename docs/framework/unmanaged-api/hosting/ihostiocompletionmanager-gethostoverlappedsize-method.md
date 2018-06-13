---
title: IHostIoCompletionManager::GetHostOverlappedSize メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6713fdb822babf607752c1823a32dae43a7d567e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439605"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize メソッド
ホストが、I/O 要求に追加しようとしています。 カスタム データのサイズを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcbSize`  
 [out]Win32 のサイズだけでなく、共通言語ランタイム (CLR) を割り当てる必要がありますバイト数へのポインター`OVERLAPPED`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 Windows api のプラットフォームのすべての非同期 I/O 呼び出しかかる Win32`OVERLAPPED`ファイル ポインターの位置などの情報を提供するオブジェクト。 状態を維持するためには、通常 I/O の非同期呼び出しを実行するアプリケーションは、カスタム データを構造に追加します。 `GetHostOverlappedSize` および[ihostiocompletionmanager::initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)ホストをこのようなカスタム データを含む機会を提供します。  
  
 CLR の呼び出し、`GetHostOverlappedSize`ホストに追加しようとしました。 カスタムのデータのサイズを決定するメソッド、`OVERLAPPED`オブジェクト。  
  
> [!NOTE]
>  `GetHostOverlappedSize` 1 回だけ呼び出されます。 ホストのカスタム データは、すべての I/O 要求のサイズと同じである必要があります。  
  
> [!IMPORTANT]
>  サイズ、`OVERLAPPED`オブジェクト自体がの値に含まれていない`pcbSize`です。  
  
 詳細については、`OVERLAPPED`構造体、Windows プラットフォームのドキュメントを参照してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.NativeOverlapped>  
 [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
