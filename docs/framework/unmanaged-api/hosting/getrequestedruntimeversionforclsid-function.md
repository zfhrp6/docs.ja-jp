---
title: "GetRequestedRuntimeVersionForCLSID 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be55754bc626ce24c51eec7b10d9f46aec92cfe5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID 関数
適切な共通言語ランタイム (CLR) のバージョン情報に、指定したクラスを取得`CLSID`です。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。  
  
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
|E_POINTER|`dwLength`null、または`cchBuffer`バージョン文字列を保持するために十分な大きさが、`pVersion`が null です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [サポートされなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
