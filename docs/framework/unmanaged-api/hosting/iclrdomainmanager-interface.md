---
title: ICLRDomainManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b8dd67cb7dff4bec5bab192a08461ef13fcbd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436359"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager インターフェイス
ホストが初期化プロパティを指定して既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーを指定できるようにします。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetAppDomainManagerType メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|派生する型を指定、<xref:System.AppDomainManager?displayProperty=nameWithType>の既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーのクラスです。|  
|[SetPropertiesForDefaultAppDomain メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|既定のアプリケーション ドメインを初期化するために使用されるプロパティを設定します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスのインスタンスを取得する、 [iclrcontrol::getclrmanager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) IID マネージャーの種類を持つメソッド`IID_ICLRDomainManager`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
