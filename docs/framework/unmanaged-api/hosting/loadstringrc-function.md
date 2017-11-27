---
title: "LoadStringRC 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a>LoadStringRC 関数
現在のスレッドの既定のカルチャを使用して、HRESULT 値をエラー メッセージに変換します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iResourceID`  
 [in]HRESULT。  
  
 `szBuffer`  
 [out]正常完了時にエラー メッセージを格納するバッファー。  
  
 `iMax`  
 [in]エラー メッセージ バッファーのサイズ。  
  
 `bQuiet`  
 [in]無視されます。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の値に加え、WinError.h で定義されている標準のコンポーネント オブジェクト モデル (COM) エラー コードを返します。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_INVALIDARG|`szBuffer`null または`iMax`はゼロ (0) です。|  
  
## <a name="remarks"></a>コメント  
 メソッドが正常に完了しない場合`szBuffer`空の文字列が含まれています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll と Mscorwks.dll です。 Mscorwks.dll の代わりに MSCorEE.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [LoadStringRCEx 関数](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [推奨されなくなった CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
