---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690287bf54f98c19298504ee3058a59ef88a87f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433162"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime メソッド
すべてレガシ共通言語ランタイム (CLR) バージョン 2 のアクティブ化ポリシーの決定の現在のランタイムにバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の Hresult を返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|バインディングが成功したか、このランタイムがレガシ CLR バージョン 2 のアクティブ化のポリシー実行時に既にバインドされています。|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|異なるランタイムは、従来の CLR バージョン 2 のアクティブ化ポリシーに既にバインドされています。|  
  
## <a name="remarks"></a>コメント  
 現在のランタイムがすべてレガシ CLR バージョン 2 のアクティブ化ポリシーの決定に既にバインドされている場合 (たとえばを使用して、`useLegacyV2RuntimeActivationPolicy`属性を[\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)構成ファイルで)、このメソッドエラーの結果を返しません代わりと同様、メソッドがレガシ アクティブ化ポリシーを正常にバインドしたかどうかに、結果は S_OK です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [\<startup> 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
