---
title: StrongNameSignatureVerificationFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 919c746b738246d76e90730c42882bfdd3ac6edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458722"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 関数
メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。  
  
 この関数は廃止されました。 使用して、 [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbBase`  
 [in]マップされているアセンブリ マニフェストの相対仮想アドレス。  
  
 `dwLength`  
 [in]マップされたイメージのバイト単位のサイズ。  
  
 `dwInFlags`  
 [in]検証動作を制御するフラグ。 次の値がサポートされています。  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) のレジストリ設定を上書きする必要がある場合でも強制的に検証します。  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - これが初めてこのイメージ上で実行する検証であることを指定します。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) のキャッシュで管理者特権を持っているユーザーにのみアクセスを許可することを指定します。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) のアセンブリが現在のユーザーのみアクセスできることを指定します。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) のキャッシュはしないことを指定のアクセス制限を保証します。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグのために予約されています。  
  
 `pdwOutFlags`  
 [out]追加の出力情報に対するフラグです。 次の値がサポートされています。  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値は設定`false`レジストリ設定のために、検証が成功したことを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`です。  
  
## <a name="remarks"></a>コメント  
 場合、`StrongNameSignatureVerificationFromImage`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameSignatureVerificationFromImage メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
