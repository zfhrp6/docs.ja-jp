---
title: IEnumDefinitionIdentity インターフェイス
ms.date: 03/30/2017
api_name:
- IEnumDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IEnumDefinitionIdentity
helpviewer_keywords:
- IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34186ee8825c0981ec095cf855c76ff5f800907d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ienumdefinitionidentity-interface"></a>IEnumDefinitionIdentity インターフェイス
コレクションの列挙子の役割を果たす`IDefinitionIdentity`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
IEnumDefinitionIdentity : IUnknown {  
  
    HRESULT Clone (  
        [out] IEnumDefinitionIdentity **ppIEnumDefinitionIdentity  
    );  
  
    HRESULT Next (  
        [in]  ULONG               celt,  
        [out, length_is(celt), size_is(*pceltWritten)]  
              IDefinitionIdentity *rgpIDefinitionIdentity[],  
        [out] ULONG               *pceltWritten  
    );  
  
    HRESULT Reset ();  
  
    HRESULT Skip (  
        [in] ULONG celt  
    );  
  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|`IEnumDefinitionIdentity::Clone`|新しいインターフェイス ポインターを取得`IEnumDefinitionIdentity`これと同じメンバーを格納しているオブジェクト`IEnumDefinitionIdentity`です。|  
|`IEnumDefinitionIdentity::Next`|指定した数を取得`IDefinitionIdentity`オブジェクト、現在の位置で開始します。|  
|`IEnumDefinitionIdentity::Reset`|これの先頭に、命令ポインターを移動`IEnumDefinitionIdentity`です。|  
|`IEnumDefinitionIdentity::Skip`|指定した数の現在位置の要素では、命令ポインターを前方を移動します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
