---
title: IMetaDataDispenser::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0fb805e3292d90fd5f9562d9b0b8fcc31f84ec7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449365"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope メソッド
既存のディスク上のファイルを開き、そのメタデータをメモリにマップします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szScope`  
 [in]開かれるファイルの名前。 ファイルは、共通言語ランタイム (CLR) メタデータを含める必要があります。  
  
 `dwOpenFlags`  
 [in]値、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)開くのためのモード (読み取り、書き込み、およびなど) を指定する列挙体です。  
  
 `riid`  
 [in]返される; 必要なメタデータ インターフェイスの IID呼び出し元は (読み取り) をインポートまたは (書き込み) メタデータを生成するインターフェイスを使用します。  
  
 値`riid`"import"や「生成」のインターフェイスのいずれかを指定する必要があります。 有効な値は IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。  
  
 `ppIUnk`  
 [out]返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>コメント  
 「インポート」インターフェイスの 1 つからメソッドを使用または「生成」インターフェイスのいずれかからメソッドを使用する追加のメタデータのメモリ内のコピーを照会できます。  
  
 ターゲット ファイルには、CLR メタデータが含まれていない場合、`OpenScope`メソッドは失敗します。  
  
 .NET Framework バージョン 1.0 および 1.1 の場合は、スコープが開かれてで`dwOpenFlags`ofRead に設定するは共有の条件に適合します。 つまり、後続の場合を呼び出す`OpenScope`既に開かれているファイルの名前、パスは、既存のスコープが再利用され、データ構造体の新しいセットは作成されません。 ただし、この共有のため問題が発生することができます。  
  
 .NET Framework version 2.0 では、スコープを開くと`dwOpenFlags`ofRead に設定が共有されなくなります。 OfReadOnly 値を使用して、共有するスコープを許可します。 スコープを共有している場合は、「読み取り/書き込み」メタデータ インターフェイスを使用するクエリは失敗します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataDispenser インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 [IMetaDataDispenserEx インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [IMetaDataAssemblyImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [IMetaDataEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
