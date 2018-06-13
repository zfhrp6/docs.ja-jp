---
title: IReferenceAppId インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429518"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId インターフェイス
現在のスコープ内のアプリケーションの一意識別子への参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|これによって参照されているアプリケーションのコードの識別子の文字列表記にポインターを取得`IReferenceAppId`です。|  
|`IReferenceAppId::put_CodeBase`|これによって参照されているアプリケーションのコードの識別子を設定`IReferenceAppId`です。|  
|`IReferenceAppId::EnumAppPath`|インターフェイス ポインターを取得、`IEnumReferenceIdentity`インスタンスを含む、 `IReferenceIdentity` this のメンバーを表すインスタンス`IReferenceAppId`です。|  
|`IReferenceAppId::get_SubscriptionId`|このサブスクリプションのトークンの id の文字列形式へのポインターを取得`IReferenceAppId`です。|  
|`IReferenceAppId::put_SubscriptionId`|このサブスクリプションのトークンの識別子を設定`IReferenceAppId`に指定した文字列値です。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
