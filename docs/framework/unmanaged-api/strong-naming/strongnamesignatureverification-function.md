---
title: StrongNameSignatureVerification 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c888c32a0b40d2458a919613e35ca9d1d830c4f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459236"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 関数
指定されたパスにあるアセンブリ マニフェストに指定したフラグに従って検証される厳密な名前の署名が含まれるかどうかを示す値を取得します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]確認するアセンブリのポータブル実行可能ファイル (.dll または .exe) ファイルへのパス。  
  
 `dwInFlags`  
 [in]検証動作を変更するフラグを設定します。 次の値がサポートされています。  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) のレジストリ設定を上書きする必要がある場合でも強制的に検証します。  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - これが初めてマニフェストの検証であることを指定します。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) のキャッシュで管理者特権を持っているユーザーにのみアクセスを許可することを指定します。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) のアセンブリが現在のユーザーのみアクセスできることを指定します。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) のキャッシュはしないことを指定のアクセス制限を保証します。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグのために予約されています。  
  
 `pdwOutFlags`  
 [out]厳密な名前の署名が検証されたかどうかを示すフラグです。 次の値がサポートされています。  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値は設定`false`レジストリ設定のために、検証が成功したことを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 検証が成功した場合それ以外の場合、`false`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)  
 [StrongNameSignatureVerificationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
