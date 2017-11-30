---
title: "ICLRStrongName::StrongNameSignatureGenerationEx メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGenerationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b0527be680ed755366f77593e4dc7e1dea830c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx メソッド
指定したフラグに基づいて、指定したアセンブリの厳密な名前の署名を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]厳密な名前の署名の生成対象となるアセンブリのマニフェストを格納しているファイルへのパス。  
  
 `wszKeyContainer`  
 [in]公開/秘密キー ペアを格納するキー コンテナーの名前。  
  
 場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーのペアは、ファイルの署名に使用されます。  
  
 場合`pbKeyBlob`が null でないと見なされますのキー ペア キー バイナリ ラージ オブジェクト (BLOB) に含まれています。  
  
 `pbKeyBlob`  
 [in]公開/秘密キー ペアへのポインター。 Win32 によって作成された形式では、このペア`CryptExportKey`関数。 場合`pbKeyBlob`は null、によって指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。  
  
 `cbKeyBlob`  
 [in]サイズをバイト単位での`pbKeyBlob`します。  
  
 `ppbSignatureBlob`  
 [out]共通言語ランタイムをするには、署名を返します場所へのポインター。 場合`ppbSignatureBlob`が null の場合、ランタイム、署名ファイルに格納で指定された`wszFilePath`です。  
  
 場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。 呼び出し元が使用して、この領域を解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッドです。  
  
 `pcbSignatureBlob`  
 [out]返された署名のバイト単位のサイズ。  
  
 `dwFlags`  
 [in]1 つ以上の次の値。  
  
-   `SN_SIGN_ALL_FILES`(0x00000001) - リンクされたモジュールのすべてのハッシュを再計算します。  
  
-   `SN_TEST_SIGN`(0x00000002) - テスト アセンブリに署名します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。  
  
## <a name="remarks"></a>コメント  
 Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名は、いずれか、ファイルに直接格納または呼び出し元に返されます。  
  
 場合`SN_SIGN_ALL_FILES`が指定されているが、公開キーは含まれません (両方`pbKeyBlob`と`wszFilePath`が null)、リンクされたモジュールのハッシュが再計算されますが、アセンブリは、再署名することはありません。  
  
 場合`SN_TEST_SIGN`を指定すると、共通言語ランタイム ヘッダーは、アセンブリは厳密な名前で署名されていることを示すためには変更されません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
