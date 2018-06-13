---
title: ICorDebugModule::GetMetaDataInterface メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef23f2b128b1e5393c5104b6e33758882b34882
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420883"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface メソッド
モジュールのメタデータの検査に使用できるメタデータ インターフェイス オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `riid`  
 [in]メタデータ インターフェイスを指定する参照の ID です。  
  
 `ppObj`  
 [out]アドレスへのポインター、`T:IUnknown`のいずれかであるオブジェクトを[メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)です。  
  
## <a name="remarks"></a>コメント  
 デバッガーが使用できる、`GetMetaDataInterface`モジュールの場合、そのモジュールを編集するために手順を実行する必要がありますが、元のメタデータのコピーを作成するメソッド。 デバッガーの呼び出し`GetMetaDataInterface`を取得する、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)インターフェイス オブジェクト、モジュールの呼び出し、 [imetadataemit::savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)をメモリにモジュールのメタデータのコピーを保存します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ](../../../../docs/framework/unmanaged-api/metadata/index.md)
