---
title: "IMetaDataEmit::SetEventProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitseteventprops-method"></a>IMetaDataEmit::SetEventProps メソッド
前回の呼び出しによって定義されたイベントの指定した機能の更新を設定または[imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ev`  
 [in]イベント トークンです。  
  
 `dwEventFlags`  
 [in]イベントのフラグです。 これは、ビットマスク`CorEventAttr`値。  
  
 `tkEventType`  
 [in]イベント クラスに対してトークンです。 これは、いずれか、`mdTypeDef`または`mdTypeRef`トークンです。  
  
 `mdAddOn`  
 [in]イベント、または null にサブスクライブするために使用するメソッド。  
  
 `mdRemoveOn`  
 [in]イベント、または null をアンサブスク ライブする方法。  
  
 `mdFire`  
 [in]イベントを発生させる (派生クラス) によって使用されるメソッド。  
  
 `rmdOtherMethods[]`  
 [in]イベントに関連付けられたその他のメソッドのトークンの配列。 配列の最後の要素である必要があります`mdMethodDefNil`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
