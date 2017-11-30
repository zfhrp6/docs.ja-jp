---
title: "StrongNameSignatureGeneration 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureGeneration
helpviewer_keywords: StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26900b73e4c0b8b7501a59c3706966df5cf46120
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 関数
指定したアセンブリの厳密な名前の署名を生成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
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
  
 場合`ppbSignatureBlob`が null でない、共通言語ランタイムは領域を割り当てますを返す、署名します。 呼び出し元が使用して、この領域を解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。  
  
 `pcbSignatureBlob`  
 [out]返された署名のバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に終了します。それ以外の場合、`false`です。  
  
## <a name="remarks"></a>コメント  
 Null を指定する`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名があることができます、ファイルに直接格納または呼び出し元に返されます。  
  
 場合、`StrongNameSignatureGeneration`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
