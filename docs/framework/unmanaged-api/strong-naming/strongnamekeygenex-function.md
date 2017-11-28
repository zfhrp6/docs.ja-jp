---
title: "StrongNameKeyGenEx 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyGenEx
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyGenEx
helpviewer_keywords: StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87841c230c71650f822a6cb2f6cc3f3c17c2ef35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx 関数
厳密な名前に使用するため、指定されたキー サイズで新しい公開/秘密キー ペアを生成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszKeyContainer`  
 [in]要求されたキー コンテナーの名前です。 `wszKeyContainer`一時的な名前を生成する場合は null か空でない文字列である必要があります。  
  
 `dwFlags`  
 [in]登録キーのままにするかどうかを指定します。 次の値がサポートされています。  
  
-   0x00000000 の際に使用される`wszKeyContainer`は一時的なキー コンテナー名を生成する場合は null です。  
  
-   0x00000001 (`SN_LEAVE_KEY`)-キーを左に登録する必要がありますを指定します。  
  
 `dwKeySize`  
 [in]ビット単位のキーの要求されたサイズ。  
  
 `ppbKeyBlob`  
 [out]返された公開/秘密キー ペア。  
  
 `pcbKeyBlob`  
 [out]サイズをバイト単位での`ppbKeyBlob`します。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に終了します。それ以外の場合、`false`です。  
  
## <a name="remarks"></a>コメント  
 .NET Framework のバージョン 1.0 および 1.1 が必要な`dwKeySize`厳密な名前でアセンブリに署名する 1024 ビットのバージョン 2.0 には、2048 ビットのキーのサポートが追加されています。  
  
 呼び出す必要があります、キーが取得された後、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。  
  
 場合、`StrongNameKeyGenEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameKeyGenEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [StrongNameKeyGen メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
