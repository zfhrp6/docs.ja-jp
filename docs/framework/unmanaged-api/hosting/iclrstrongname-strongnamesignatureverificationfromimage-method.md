---
title: ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60dbb8d8461015c791a70d6c2617b1c81e5ba17f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434269"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a>ICLRStrongName::StrongNameSignatureVerificationFromImage メソッド
メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
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
 `S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
