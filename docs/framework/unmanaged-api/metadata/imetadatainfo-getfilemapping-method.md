---
title: IMetaDataInfo::GetFileMapping メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 562b6fcd015441ce5eb6b5f0ab7a4f361bb229c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449430"
---
# <a name="imetadatainfogetfilemapping-method"></a>IMetaDataInfo::GetFileMapping メソッド
メモリの領域、マップされたファイルとマッピングの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppvData`  
 [out]マップされたファイルの先頭へのポインター。  
  
 `pcbData`  
 [out]マップ領域のサイズ。 場合`pdwMappingType`は`fmFlat`、これは、ファイルのサイズ。  
  
 `pdwMappingType`  
 [out]A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)マッピングの種類を示す値。 現在の実装の共通言語ランタイム (CLR) 常に返します`fmFlat`です。 その他の値は、将来の使用に備えて予約されています。 ただし、その他の値は、将来のバージョンで有効にすることがありますか、サービス リリースために、常に、返される値を確認してください。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|すべての出力が入力されます。|  
|`E_INVALIDARG`|引数の値として NULL が渡されました。|  
|`COR_E_NOTSUPPORTED`|CLR 実装には、メモリ領域に関する情報を提供できません。 これは、次の理由が考えられます。<br /><br /> メタデータ スコープが開かれた、`ofWrite`または`ofCopyMemory`フラグ。<br />-なしのメタデータ スコープが開かれて、`ofReadOnly`フラグ。<br />- [Imetadatadispenser::openscopeonmemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md)を開くには、ファイルのメタデータ部分だけにメソッドが使用されました。<br />-ファイルは、ポータブル実行可能 (PE) ファイルではありません。 **注:** CLR 実装に依存してこれらの条件とする可能性がありますが脆弱になる将来のバージョンの CLR です。|  
  
## <a name="remarks"></a>コメント  
 メモリを`ppvData`へのポインターが有効ではだけの基になるメタデータ スコープが開かれています。  
  
 このメソッドを呼び出してメモリ、ディスク上のファイルのメタデータをマップするときに、作業をするために、 [imetadatadispenser::openscope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md)を指定する必要があります、メソッド、`ofReadOnly`フラグとする必要がありますを指定しない、`ofWrite`または`ofCopyMemory`フラグ。  
  
 各スコープのファイル マッピングの種類の選択は、CLR の特定の実装に固有です。 ユーザーがこれを設定できません。 現在の実装、CLR の常に返します`fmFlat`で`pdwMappingType`が変わることが将来のバージョンの CLR または将来の指定したバージョンのサービス リリースです。 返される値を常に確認する必要があります`pdwMappingType`のため、さまざまな種類はさまざまなレイアウト、およびオフセットします。  
  
 3 つのパラメーターのいずれかに NULL を渡すことはサポートされていません。 このメソッドを返します`E_INVALIDARG`出力のいずれもがいっぱいになるとします。 マッピングの種類や領域のサイズを無視すると、プログラムが異常終了が発生することができます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IMetaDataInfo インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 [CorFileMapping 列挙型](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
