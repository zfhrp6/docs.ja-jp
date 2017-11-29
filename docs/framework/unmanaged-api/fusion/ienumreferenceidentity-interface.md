---
title: "IEnumReferenceIdentity インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity インターフェイス
コレクションの列挙子の役割を果たす`IReferenceIdentity`オブジェクト。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|新しいインターフェイス ポインターを取得`IEnumReferenceIdentity`これと同じメンバーを格納している`IEnumReferenceIdentity`です。|  
|`IEnumReferenceIdentity::Next`|指定した数を取得`IReferenceIdentity`オブジェクト、現在の位置で開始します。|  
|`IEnumReferenceIdentity::Reset`|これの先頭に、命令ポインターを移動`IEnumReferenceIdentity`です。|  
|`IEnumReferenceIdentity::Skip`|指定した数の現在位置の要素では、命令ポインターを前方を移動します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
