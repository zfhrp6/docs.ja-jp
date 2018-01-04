---
title: "GetHashFromFile 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromFile
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromFile
helpviewer_keywords: GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 関数
指定されたファイルの内容のハッシュを生成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szFilePath`  
 [in]ハッシュには、ファイルの名前。  
  
 `piHashAlg`  
 [入力、出力].ハッシュを生成するときに使用するアルゴリズムです。 有効なアルゴリズムを使用して、Win32 CryptoAPI で定義されています。 場合`piHashAlg`は 0、CALG_SHA 1 が使用される既定のアルゴリズムに設定します。  
  
 `pbHash`  
 [out]生成されたハッシュを含むバイト配列。  
  
 `cchHash`  
 [in]バッファーの最大サイズを`pbHash`を指します。  
  
 `pchHash`  
 [out]サイズ (バイト単位)、返された`pbHash`です。  
  
## <a name="remarks"></a>コメント  
 この関数は、同じ[GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)ファイル名の指定は、Unicode ではなく ANSI ことを除き、します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [GetHashFromFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [GetHashFromFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
