---
title: ICLRStrongName::StrongNameGetBlob メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81e2c59a538bd436606c226855c002cecd501e33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a>ICLRStrongName::StrongNameGetBlob メソッド
指定したアドレスに実行可能ファイルのバイナリ表現を指定したバッファーに設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]読み込まれる実行可能ファイルへの有効なパス。  
  
 `pbBlob`  
 [in]実行可能ファイルの読み込み先となるバッファー。  
  
 `pcbBlob`  
 [入力、出力].最大サイズ (バイト単位) を要求した`pbBlob`です。 関数が戻るとき、実際のサイズ (バイト単位) での`pbBlob`します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [StrongNameGetBlobFromImage メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
