---
title: IHostSecurityManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f60730fedef4876f81f078f811104777050175
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440256"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager インターフェイス
アクセスと実行中のスレッドのセキュリティ コンテキストを制御できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetSecurityContext メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|要求された取得[IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)ホストからです。|  
|[ImpersonateLoggedOnUser メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|要求の現在のユーザー id の資格情報を使用してコードを実行します。|  
|[OpenThreadToken メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|現在のスレッドに関連付けられている随意アクセス トークンを開きます。|  
|[RevertToSelf メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|現在のユーザー id の権限の借用を終了し、元のスレッド トークンを返します。|  
|[SetSecurityContext メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|現在実行中のスレッドのセキュリティ コンテキストを設定します。|  
|[SetThreadToken メソッド](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|現在実行中のスレッドのハンドルを設定します。|  
  
## <a name="remarks"></a>コメント  
 ホストは、共通言語ランタイム (CLR) とユーザー コードの両方でスレッド トークンへのすべてのコード アクセスを制御できます。 ように、完全なセキュリティ コンテキスト情報は、非同期操作または制限付きのコード アクセス権を持つコード ポイントを越えて渡されます。 `IHostSecurityContext` このが CLR に対して非透過的セキュリティ コンテキスト情報をカプセル化します。  
  
 CLR では、マネージ スレッドのコンテキストを内部的に処理します。 プロセスに固有のクエリを実行`IHostSecurityManager`次の状況で。  
  
-   ファイナライザー スレッドでファイナライザーの実行中です。  
  
-   実行中にクラスとモジュール コンス トラクター。  
  
-   呼び出しで、ワーカー スレッドで非同期の時点で、 [ihostthreadpoolmanager::queueuserworkitem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)メソッドです。  
  
-   I/O 完了ポートの使用中です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
