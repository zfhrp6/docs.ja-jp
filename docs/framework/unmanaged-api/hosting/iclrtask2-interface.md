---
title: ICLRTask2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed0d2ff3b64bab026087e13d54314eca86181d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrtask2-interface"></a>ICLRTask2 インターフェイス
すべての機能を提供、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイスです。 さらに、現在のスレッドで遅延するスレッドの中止できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginPreventAsyncAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|新しいスレッドの遅延は、現在のスレッドで要求を中止します。|  
|[EndPreventAsyncAbort メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|新しい許可または保留中のスレッドで発生するスレッドの中止の要求を現在のスレッドの中止します。|  
  
## <a name="remarks"></a>コメント  
 `ICLRTask2`インターフェイスが継承、`ICLRTask`インターフェイスおよびホストが失敗する必要がありますしないコードの領域を保護する、スレッドの中止を延期できるようにするメソッドを追加します。 呼び出す`BeginPreventAsyncAbort`した現在のスレッドと呼び出し元の遅延スレッドの中止のカウンターをインクリメント`EndPreventAsyncAbort`デクリメントことです。 呼び出す`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`入れ子にすることができます。 カウンターは、0 より大きい値が、限り、現在のスレッドのスレッドの中止が遅延されます。  
  
 場合を呼び出す`BeginPreventAsyncAbort`と`EndPreventAsyncAbort`が対になっていない、可能であればどのスレッドで中止を現在のスレッドに配信できない状態になります。  
  
 遅延時間はそれ自体を中止するスレッドの受け入れられません。  
  
 この機能によって公開される機能は、仮想マシン (VM) で内部使用されます。 これらのメソッドの誤用によっては、VM で未定義の動作があります。 たとえば、呼び出し`EndPreventAsyncAbort`最初呼び出さず`BeginPreventAsyncAbort`VM がインクリメントしていたときに、カウンターをゼロに設定でした。 同様に、内部カウンターは、オーバーフローはチェックされません。 場合は、整数の上限を超えているため、ホストと VM の両方がインクリメントされますが、結果の動作は指定されません。  
  
 継承されたメンバーに関する情報の`ICLRTask`し、このインターフェイスの他の使用について、次を参照してください。、 [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)インターフェイスです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
