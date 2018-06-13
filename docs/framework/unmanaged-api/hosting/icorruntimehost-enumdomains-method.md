---
title: ICorRuntimeHost::EnumDomains メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 688e7a0fa32650aa0f626ddf40283f73ceb57156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437792"
---
# <a name="icorruntimehostenumdomains-method"></a>ICorRuntimeHost::EnumDomains メソッド
現在のプロセスで、ドメインの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hEnum`  
 [out]ドメインの列挙子。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|操作が正常に完了しました。|  
|S_FALSE|操作を完了できませんでした。|  
|E_FAIL|未知の致命的なエラーが発生しました。 メソッドには、E_FAIL が返されます、共通言語ランタイム (CLR) は、プロセスで使用可能なできなくします。 Api をホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
|HOST_E_CLRNOTAVAILABLE|CLR が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** 1.0、1.1  
  
## <a name="see-also"></a>関連項目  
 [ICorRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
