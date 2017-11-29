---
title: "IHostCrst インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a>IHostCrst インターフェイス
スレッド処理の重要なセクションのホストの表現として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Enter メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|クリティカル セクションに入ります。|  
|[Leave メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|クリティカル セクションのままにします。|  
|[SetSpinCount メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|クリティカル セクションのスピン カウントを設定します。|  
|[TryEnter メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|クリティカル セクション、およびレポートの成功または失敗をすぐに入力しようとしています。|  
  
## <a name="remarks"></a>コメント  
 `IHostCrst`などを使用して Win32 関数ではなく、共通言語ランタイム (CLR)、クリティカル セクションのホストの表現と直接通信するためには、`EnterCriticalSection`または`LeaveCriticalSection`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
