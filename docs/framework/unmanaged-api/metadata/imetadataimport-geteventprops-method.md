---
title: "IMetaDataImport::GetEventProps メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps メソッド
宣言する型、追加、デリゲートの削除メソッドと任意のフラグと関連付けられているその他のデータを含め、指定したイベント トークンによって表されるイベントのメタデータ情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ev`  
 [in]メタデータを取得するイベントを表すイベントのメタデータ トークンです。  
  
 `pClass`  
 [out]イベントを宣言するクラスを表す TypeDef トークンへのポインター。  
  
 `szEvent`  
 [out]によって参照されるイベントの名前`ev`です。  
  
 `pchEvent`  
 [in]要求された長さのワイド文字単位`szEvent`です。  
  
 `pdwEventFlags`  
 [out]ワイド文字で返される長さ`szEvent`です。  
  
 `ptkEventType`  
 [out]TypeRef または TypeDef メタデータ トークンを表すへのポインター、<xref:System.Delegate>イベントの種類。  
  
 `pmdAddOn`  
 [out]イベントのハンドラーを追加するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdRemoveOn`  
 [out]イベントのハンドラーを削除するメソッドを表すメタデータ トークンへのポインター。  
  
 `pmdFire`  
 [out]イベントを発生させるメソッドを表すメタデータ トークンへのポインター。  
  
 `rmdOtherMethod`  
 [out]イベントに関連付けられたその他のメソッドへのトークンのポインターの配列。  
  
 `cMax`  
 [in] `rmdOtherMethod` 配列の最大サイズ。  
  
 `pcOtherMethod`  
 [out]返されるトークンの数`rmdOtherMethod`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
