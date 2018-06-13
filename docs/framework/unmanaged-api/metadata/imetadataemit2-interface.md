---
title: IMetaDataEmit2 インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2
helpviewer_keywords:
- IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 418e5287852b1a8d69d310d2ba71e4f2a3b5d7bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449232"
---
# <a name="imetadataemit2-interface"></a>IMetaDataEmit2 インターフェイス
拡張、 [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)主に、ジェネリック型を処理する機能を提供するインターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineGenericParam メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md)|ジェネリック型パラメーターの定義を作成し、そのジェネリック型パラメーターにトークンを取得します。|  
|[DefineMethodSpec メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)|メソッドのジェネリックのインスタンスを作成し、定義にトークンを取得します。|  
|[GetDeltaSaveSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)|エディット コンティニュの現在のセッションに対する変更を表すために必要なデータのサイズの差を示す値を取得します。|  
|[ResetENCLog メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md)|エディット コンティニュは、ログをリセットし、新しいセッションを開始します。|  
|[SaveDelta メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedelta-method.md)|エディット コンティニュの現在のセッションからの変更を指定したファイルに保存します。|  
|[SaveDeltaToMemory メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)|エディット コンティニュの現在のセッションからの変更をメモリに保存します。|  
|[SaveDeltaToStream メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatostream-method.md)|エディット コンティニュの現在のセッションからの変更を指定したストリームに保存します。|  
|[SetGenericParamProps メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-setgenericparamprops-method.md)|指定したトークンによって参照されるジェネリック パラメーターの定義のプロパティの値を設定します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
