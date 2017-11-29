---
title: "IEnumDefinitionIdentity インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumDefinitionIdentity
helpviewer_keywords: IEnumDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: 8263e75d-251b-4abc-8a1a-c62884142232
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc1f3a46ac7da58fb2c209f833173a1bc6b32ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Isolation.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IDefinitionIdentity インターフェイス](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
