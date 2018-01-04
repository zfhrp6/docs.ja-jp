---
title: "IHostTask インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask
helpviewer_keywords: IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a>IHostTask インターフェイス
共通言語ランタイム (CLR) のタスクを管理するホストと通信できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Alert メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|要求のホストが現在のタスクを wake`IHostTask`インスタンス、タスクを中止できるようにします。|  
|[GetPriority メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|現在で表されるタスクのスレッド優先度レベルを取得`IHostTask`インスタンス。|  
|[Join メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|現在で表されるタスクまで呼び出し元のタスクをブロック`IHostTask`インスタンスが完了すると、指定した時間間隔が経過すると、または[ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)と呼びます。|  
|[SetCLRTask メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|関連付けます、 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)、現在のインスタンス`IHostTask`インスタンス。|  
|[SetPriority メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|要求スレッドの優先度を変更するホスト レベルの現在のタスクの`IHostTask`インスタンス。|  
|[Start メソッド](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|ホストが現在のタスクを移動要求`IHostTask`インスタンスを中断状態からコードを実行できる状態にします。|  
  
## <a name="remarks"></a>コメント  
 CLR によって定義されたメソッドを呼び出し、`IHostTask`セットを開始するタスク、そのスレッドの優先度レベルのようにします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
