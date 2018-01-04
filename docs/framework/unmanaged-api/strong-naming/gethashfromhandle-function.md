---
title: "GetHashFromHandle 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromHandle
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromHandle
helpviewer_keywords: GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 45acc02645f45446e37935d7fe7a455f4105d8bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromhandle-function"></a>GetHashFromHandle 関数
指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを持つファイルの内容のハッシュを生成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hFile`  
 [in]ハッシュされるファイルのハンドル。  
  
 `piHashAlg`  
 [入力、出力].ハッシュ アルゴリズムを指定する定数。 既定のアルゴリズムに 0 を使用します。  
  
 `pbHash`  
 [out]返されるハッシュ バッファー。  
  
 `cchHash`  
 [in]場合は、要求された最大サイズ`pbHash`です。  
  
 `pchHash`  
 [out]サイズ (バイト単位)、返された`pbHash`です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [GetHashFromHandle メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
