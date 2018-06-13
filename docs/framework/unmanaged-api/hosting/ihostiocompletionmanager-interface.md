---
title: IHostIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 194dcec6ea484e9cd2d3a17093c1eceb16c8f6c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440217"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager インターフェイス
共通言語ランタイム (CLR) にホストによって提供される I/O 完了ポートとやり取りできるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Bind メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|I/O 完了ポートへのハンドルにバインドします。|  
|[CloseIoCompletionPort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|事前に呼び出したを介して作成されたポートを閉じる`CreateIoCompletionPort`です。|  
|[CreateIoCompletionPort メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|要求のホストが新しい I/O 完了ポートを作成することです。|  
|[GetAvailableThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|現在の要求を処理していない I/O 完了スレッドの数を取得します。|  
|[GetHostOverlappedSize メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|ホストが、I/O 要求に追加しようとしています。 カスタム データのサイズを取得します。|  
|[GetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|I/O 要求を処理するには、ホストが割り当てることができますのスレッドの最大数を取得します。|  
|[GetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|I/O 要求を処理するには、ホストが提供するスレッドの最小数を取得します。|  
|[InitializeHostOverlapped メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|I/O 要求についてカスタム データを初期化するために営業案件にホストを提供します。|  
|[SetCLRIoCompletionManager メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|により、ホストへのインターフェイス ポインターで、 [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)インスタンスの CLR によって実装されます。|  
|[SetMaxThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|I/O 要求を処理するため、ホストに割り当てるスレッドの最大数を設定します。|  
|[SetMinThreads メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|I/O 完了をホストに割り当てる必要があるスレッドの最小数を設定します。|  
  
## <a name="remarks"></a>コメント  
 `IHostIoCompletionManager` 対応する、 `ICLRIoCompletionManager` CLR によって実装されるインターフェイス。 CLR のメソッドを呼び出します`IHostIoCompletionManager`ハンドルをホストが提供して、ホストのメソッドを呼び出して、ポートにバインドする`ICLRIoCompletionManager`I/O 要求の完了を報告します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
