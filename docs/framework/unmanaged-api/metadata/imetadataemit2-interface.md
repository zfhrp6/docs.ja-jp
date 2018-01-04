---
title: "IMetaDataEmit2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit2
helpviewer_keywords: IMetaDataEmit2 interface [.NET Framework metadata]
ms.assetid: 866dc96b-bbfc-4c0f-80c2-38ce93072106
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94180a1f844ac43d8a42be59ac4fca807a70ec70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
