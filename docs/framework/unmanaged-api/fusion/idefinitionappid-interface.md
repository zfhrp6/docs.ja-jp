---
title: "IDefinitionAppId インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247edbe300bbb93ddbdd4260109999fd33b08006
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId インターフェイス
現在のスコープで、アプリケーションを定義するコードの一意の識別子を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|このコードを表す書式設定された文字列を取得`IDefinitionAppId`オブジェクト。|  
|`IDefinitionAppId::put_Codebase`|このコード設定`IDefinitionAppId`を指定したオブジェクトの書式設定された文字列値です。|  
|`IDefinitionAppId::EnumAppPath`|インターフェイス ポインターを取得、 [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)を現在のアプリケーション パス内のアセンブリを含むオブジェクト。|  
|`IDefinitionAppId::SetAppPath`|アセンブリの指定したによって参照される値を現在のスコープでアプリケーションのパスを設定[IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)オブジェクト。|  
|`IDefinitionAppId::get_SubscriptionId`|このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IDefinitionAppId`オブジェクト。|  
|`IDefinitionAppId::put_SubscriptionId`|このサブスクリプションのトークンの識別子を設定`IDefinitionAppId`オブジェクトを指定した文字列値にします。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
