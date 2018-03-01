---
title: "IMetaDataTables インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables
helpviewer_keywords:
- IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 31272cce-506a-4f18-bcbf-01ee45e36356
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ff70e99a963c929792a73cefd6e8feaefa8b252e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables-interface"></a>IMetaDataTables インターフェイス
テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblob-method.md)|指定された列インデックスにあるバイナリ ラージ オブジェクト (BLOB) へのポインターを取得します。|  
|[GetBlobHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getblobheapsize-method.md)|BLOB ヒープのバイト単位のサイズを取得します。|  
|[GetCodedTokenInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcodedtokeninfo-method.md)|指定した行のインデックスに関連付けられているトークンの配列へのポインターを取得します。|  
|[GetColumn メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumn-method.md)|指定したテーブルのインデックスにある表で、指定された列インデックスの列に含まれる値へのポインターを取得します。|  
|[GetColumnInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getcolumninfo-method.md)|指定されたテーブルで指定された列に関するデータを取得します。|  
|[GetGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguid-method.md)|指定したインデックス位置の行から GUID を取得します。|  
|[GetGuidHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getguidheapsize-method.md)|GUID ヒープのバイト単位のサイズを取得します。|  
|[GetNextBlob メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextblob-method.md)|テーブル内には、次の BLOB のインデックスを取得します。|  
|[GetNextGuid メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextguid-method.md)|現在のテーブルの列には、次の GUID 値のインデックスを取得します。|  
|[GetNextString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextstring-method.md)|現在のテーブルの列には、次の文字列のインデックスを取得します。|  
|[GetNextUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnextuserstring-method.md)|現在のテーブルの列に [次へ] ハード コーディングされた文字列を含む行のインデックスを取得します。|  
|[GetNumTables メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getnumtables-method.md)|現在のスコープ内のテーブルの数を取得`IMetaDataTables`インスタンス。|  
|[GetRow メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getrow-method.md)|指定したテーブルのインデックスにある表で、指定した行のインデックス行を取得します。|  
|[GetString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstring-method.md)|現在参照スコープ内のテーブル列から、指定したインデックス位置文字列を取得します。|  
|[GetStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getstringheapsize-method.md)|文字列ヒープのバイト単位のサイズを取得します。|  
|[GetTableIndex メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableindex-method.md)|指定したトークンによって参照されるテーブルのインデックスを取得します。|  
|[GetTableInfo メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-gettableinfo-method.md)|指定したテーブル インデックスの名前、行のサイズ、行の数、列の数、およびテーブルのキー列のインデックスを取得します。|  
|[GetUserString メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstring-method.md)|現在のスコープ内の文字列の列で指定したインデックス位置には、ハード コーディングされた文字列を取得します。|  
|[GetUserStringHeapSize メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-getuserstringheapsize-method.md)|ユーザー文字列ヒープのバイト単位のサイズを取得します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataTables2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
