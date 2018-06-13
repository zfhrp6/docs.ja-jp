---
title: ICLRMetadataLocator::GetMetadata メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403859"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a>ICLRMetadataLocator::GetMetadata メソッド
イメージのメタデータを取得する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `imagePath`  
 [in]イメージ ファイルのパスを指定する文字列。  
  
 `imageTimestamp`  
 [in]イメージ ファイルのタイムスタンプ。  
  
 `imageSize`  
 [in]イメージ ファイルのサイズ。  
  
 `mvid`  
 [in]イメージのグローバルに一意の識別子。  
  
 `mdRva`  
 [in]メタデータの相対仮想アドレス (RVA)。 イメージのベース アドレスに対する相対パス、アドレスです。  
  
 `flags`  
 [in]将来使用するために予約されています。  
  
 `bufferSize`  
 [in]メタデータを格納するバッファーのサイズ。  
  
 `buffer`  
 [out]メタデータを格納するバッファー。  
  
 `dataSize`  
 [out]返されるメタデータのサイズ。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRMetadataLocator インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
