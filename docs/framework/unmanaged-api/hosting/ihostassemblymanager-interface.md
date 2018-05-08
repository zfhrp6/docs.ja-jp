---
title: IHostAssemblyManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c8c8d17723481fc5b41fe5f3006fe8db2c53d1ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager インターフェイス
ホストが共通言語ランタイム (CLR) またはホストに読み込む必要のあるアセンブリのセットを指定できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetAssemblyStore メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|インターフェイス ポインターを取得、 [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)ホストによって読み込まれるアセンブリの一覧を表すです。|  
|[GetNonHostStoreAssemblies メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|インターフェイス ポインターを取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)ホストに読み込む CLR が期待しているアセンブリの一覧を表すです。|  
  
## <a name="remarks"></a>コメント  
 ホストが実装する必要はありません`IHostAssemblyManager`または`IHostAssemblyStore`です。 ホストが実装する場合`IHostAssemblyManager`もに実装する必要があります`IHostAssemblyStore`です。  
  
 ランタイムを照会、`IHostAssemblyManager`を呼び出して[ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)の初期化時に、 `IID` IID_IHostAssemblyManager のです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
