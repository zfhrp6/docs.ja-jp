---
title: IReferenceIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432104"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity インターフェイス
コード オブジェクトの一意のシグネチャへの参照を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|新しいインターフェイス ポインターを取得`IReferenceIdentity`これと同じであるインスタンス`IReferenceIdentity`、指定した属性の変更を除きです。|  
|`IReferenceIdentity::EnumAttributes`|インターフェイス ポインターを取得、`IEnumIDENTITY_ATTRIBUTE`インスタンスに関連付けられた属性を含む`IReferenceIdentity`です。|  
|`IReferenceIdentity::GetAttribute`|指定した名前空間の指定した名前の属性の値を取得します。|  
|`IReferenceIdentity::SetAttribute`|指定した名前空間と、指定された値を指定した名前を持つ属性を設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
