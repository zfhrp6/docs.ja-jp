---
title: GetRequestedRuntimeVersionForCLSID 関数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d3a7168ce0ee3484384ae0e2d10ca00367fc9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432860"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 関数
適切な共通言語ランタイム (CLR) のバージョン情報に、指定したクラスを取得`CLSID`です。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `rclsid`  
 [in] `CLSID`のコンポーネントです。  
  
 `pVersion`  
 [out] 正常完了時にバージョン番号の文字列を格納するバッファー。  
  
 `cchBuffer`  
 [in] ワイド文字単位のサイズの`pVersion`バッファー。  
  
 `dwLength`  
 [out]返されたバッファーの長さ、(バイト単位)。  
  
 `dwResolutionFlags`  
 [in] CLSID_RESOLUTION_FLAGS 値のいずれか。 次の値がサポートされています。  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) 既定の相互運用機能の動作を指定する必要がありますを使用します。  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1)、レジストリが検索するかや、ポリシーに shim を適用を指定する必要がありますを適用します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|関数が正常に返されます。|  
|E_INVALIDARG|パラメーターのいずれかが無効な型または形式です。|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`バッファーがバージョン文字列全体を保持するのに十分ではありません。|  
|REGDB_E_CLASSNOTREG|指定した登録されているクラスはありません`CLSID`です。|  
|E_POINTER|`dwLength` null、または`cchBuffer`バージョン文字列を保持するために十分な大きさが、`pVersion`が null です。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
