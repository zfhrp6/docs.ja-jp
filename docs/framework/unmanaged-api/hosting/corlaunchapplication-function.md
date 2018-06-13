---
title: CorLaunchApplication 関数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a53b0a9cdcec33846f9d491e7d6567bcf9235b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428763"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication 関数
指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。  
  
 この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwClickOnceHost`  
 [in]値、 [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md)アプリケーションの起動は、ホストの種類を指定する列挙です。  
  
 `pwzAppFullName`  
 [in]起動されるアプリケーションの完全名。  
  
 `dwManifestPaths`  
 [in]アプリケーションのマニフェストのパスの数。  
  
 `ppwzManifestPaths`  
 [in]それぞれを指定しますが起動されるアプリケーションのマニフェストへのパス、文字列の配列。  
  
 `dwActivationData`  
 [in]起動されるアプリケーションのライセンス認証データ項目の数。  
  
 `ppwzActivationData`  
 [in]起動されるアプリケーションのライセンス認証データ項目は、それぞれが、文字列の配列。  
  
 `lpProcessInformation`  
 [out]アプリケーションが読み込まれているプロセスに関する情報へのポインター。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
