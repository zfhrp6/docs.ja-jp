---
title: "ICLRStrongName::StrongNameSignatureGeneration メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGeneration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 739dc0b08955b774f7fa15c3c346ec889f717dd2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration メソッド
指定したアセンブリの厳密な名前の署名を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。  
  
 `wszKeyContainer`  
 [in]公開/秘密キー ペアを格納するキー コンテナーの名前。  
  
 場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。  
  
 場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。  
  
 キーは、1024 ビットの Rivest-shamir-adleman (RSA) 署名キーである必要があります。 この時点では、その他の種類のキーはサポートされません。  
  
 `pbKeyBlob`  
 [in]公開/秘密キー ペアへのポインター。 Win32 によって作成された形式では、このペア`CryptExportKey`関数。 場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。  
  
 `cbKeyBlob`  
 [in]サイズをバイト単位での`pbKeyBlob`します。  
  
 `ppbSignatureBlob`  
 [out]共通言語ランタイムをするには、署名を返します場所へのポインター。 場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。  
  
 場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。 呼び出し元を使用してこの領域を解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドです。  
  
 `pcbSignatureBlob`  
 [out]返された署名のバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。  
  
## <a name="remarks"></a>コメント  
 Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名があることができます、ファイルに直接格納または呼び出し元に返されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
