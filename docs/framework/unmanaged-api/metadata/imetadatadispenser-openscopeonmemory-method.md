---
title: IMetaDataDispenser::OpenScopeOnMemory メソッド
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
caps.latest.revision: 11
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1d206863736387df04157ed752a6269b22a884b9
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a>IMetaDataDispenser::OpenScopeOnMemory メソッド
既存のメタデータを含んでいるメモリの領域を開きます。 つまり、このメソッドは、既存のデータはメタデータとして扱われますメモリの指定された領域を開きます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pData`  
 [in]メモリ領域の開始アドレスを指定するポインター。  
  
 `cbData`  
 [in]\(バイト単位) のメモリ領域のサイズ。  
  
 `dwOpenFlags`  
 [in]値、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)開くのためのモード (読み取り、書き込み、およびなど) を指定する列挙体です。  
  
 `riid`  
 [in]返される; 必要なメタデータ インターフェイスの IID呼び出し元は (読み取り) をインポートまたは (書き込み) メタデータを生成するインターフェイスを使用します。  
  
 値`riid`"import"や「生成」のインターフェイスのいずれかを指定する必要があります。 有効な値は IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。  
  
 `ppIUnk`  
 [out]返されたインターフェイスへのポインター。  
  
## <a name="remarks"></a>コメント  
 「インポート」インターフェイスの 1 つからメソッドを使用または「生成」インターフェイスのいずれかからメソッドを使用する追加のメタデータのメモリ内のコピーを照会できます。  
  
 `OpenScopeOnMemory`メソッドがに似ていますが、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)メソッド、関心のあるメタデータは、ディスク上のファイルではなく、メモリ内に既に存在する点を除いて。  
  
 メモリの対象領域に共通言語ランタイム (CLR) メタデータが含まれていない場合、`OpenScopeOnMemory`メソッドは失敗します。  
  
## <a name="requirements"></a>要件  
 **Platform:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
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
