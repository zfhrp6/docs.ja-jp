---
title: GetHashFromFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00ee1139b4b8340a73740117b74208a6a1f6b639
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461592"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 関数
Unicode 文字列で指定されたファイルの内容のハッシュを生成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]ハッシュには、ファイルの Unicode の名前。  
  
 `piHashAlg`  
 [入力、出力].ハッシュを生成するときに使用するアルゴリズムです。 有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。 場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。  
  
 `pbHash`  
 [out]生成されたハッシュを含むバイト配列。  
  
 `cchHash`  
 [in]バッファーの最大サイズを指す`pbHash`です。  
  
 `pchHash`  
 [out]サイズをバイト単位での`pbHash`します。  
  
## <a name="remarks"></a>コメント  
 この関数は、同じ[GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)ファイル名の指定は、ANSI ではなく Unicode ことを除き、します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [GetHashFromFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [GetHashFromFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
