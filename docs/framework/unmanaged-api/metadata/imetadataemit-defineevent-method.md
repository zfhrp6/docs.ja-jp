---
title: "IMetaDataEmit::DefineEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf790ce270565abaf1d91e54c9e3569a50ab3435
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefineevent-method"></a>IMetaDataEmit::DefineEvent メソッド
指定したメタデータ シグネチャを持つイベントの定義を作成し、そのイベント定義トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `td`  
 [in]ターゲット クラスまたはインターフェイスのトークンです。 これは、いずれか、`mdTypeDef`または`mdTypeDefNil`トークンです。  
  
 `szEvent`  
 [in]イベントの名前。  
  
 `dwEventFlags`  
 [in]イベントのフラグです。  
  
 `tkEventType`  
 [in]イベント クラスに対してトークンです。 これは、 `mdTypeDef`、 `mdTypeRef`、または`mdTokenNil`トークンです。  
  
 `mdAddOn`  
 [in]イベント、または null にサブスクライブするために使用するメソッド。  
  
 `mdRemoveOn`  
 [in]イベント、または null をアンサブスク ライブする方法。  
  
 `mdFire`  
 [in]イベントを発生させる (派生クラス) によって使用されるメソッド。  
  
 `rmdOtherMethods[]`  
 [in]イベントに関連付けられたその他のメソッドのトークンの配列。 配列はで終了、`mdMethodDefNil`トークンです。  
  
 `pmdEvent`  
 [out]イベントに割り当てられたメタデータ トークン。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
