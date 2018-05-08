---
title: GetAssemblyIdentityFromFile 関数
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ea151417a1cb53104ec29fff1e76e21f82ec9bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile 関数
ポインターを取得、`IUnknown`指定したオブジェクト`IID`のアセンブリにある指定したファイル パス。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzFilePath`  
 [in]要求されたアセンブリに有効なパスです。  
  
 `riid`  
 [in]`IID`のインターフェイスを返します。  
  
 `ppIdentity`  
 [out]返されたインターフェイス ポインター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 <<!--zzxref:IUnknown --> `IUnknown`>  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
