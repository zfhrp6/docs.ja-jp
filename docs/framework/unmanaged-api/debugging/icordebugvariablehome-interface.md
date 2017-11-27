---
title: "ICorDebugVariableHome インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorDebugVariableHome
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome
helpviewer_keywords: ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ea8f4033a6b0878288c49d6f6d964eb40675162d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome インターフェイス
ローカル変数または関数の引数を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetArgumentIndex メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|関数の引数のインデックスを取得します。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|インスタンスを取得します"ICorDebugCode"を含むこの`ICorDebugVariableHome`オブジェクト。|  
|[GetLiveRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|この変数がアクティブ、ネイティブな範囲を取得します。|  
|[GetLocationType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|変数のネイティブの場所の種類を取得します。|  
|[GetOffset メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|変数のベース レジスタからのオフセットを取得します。|  
|[GetRegister メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|場所の種類を持つ変数を格納するレジスタを取得`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。|  
|[GetSlotIndex メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|ローカル変数のマネージ スロット インデックスを取得します。|  
  
## <a name="example"></a>例  
 次のコード片では、 [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)という名前のオブジェクト`pCode4`です。  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugVariableHomeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
