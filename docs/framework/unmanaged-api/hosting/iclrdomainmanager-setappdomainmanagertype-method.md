---
title: "ICLRDomainManager::SetAppDomainManagerType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDomainManager.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c94da8295a0ebb96d45e3a8f122d96bc2126c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType メソッド
派生する型を指定、<xref:System.AppDomainManager?displayProperty=nameWithType>の既定のアプリケーション ドメインを初期化するために使用されるアプリケーション ドメイン マネージャーのクラスです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszAppDomainManagerAssembly`  
 [in]アプリケーション ドメイン マネージャーの種類; を含むアセンブリの表示名例:"AdMgrExample、バージョン 1.0.0.0、Culture = neutral, PublicKeyToken = 6856bccf150f00b3 を ="。  
  
 `wszAppDomainManagerType`  
 [in]名前空間を含む、アプリケーション ドメイン マネージャーの型名。  
  
 `dwInitializeDomainFlags`  
 [in]組み合わせた[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)アプリケーション ドメイン マネージャーに関する情報を提供する列挙値。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
  
## <a name="remarks"></a>コメント  
 現在、のみ定義されている値を`dwInitializeDomainFlags`は`eInitializeNewDomainFlags_NoSecurityChanges`、これによりは、共通言語ランタイム (CLR) の実行中のセキュリティ設定をアプリケーション ドメイン マネージャーが変更はこと、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッドです。 これにより、条件付きのアセンブリの読み込みを最適化するために CLR <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) 属性です。 このアセンブリのセットの推移的閉包が大きい場合は、起動時間が大幅に向上をこれがあります。  
  
> [!IMPORTANT]
>  ホストを指定する場合`eInitializeNewDomainFlags_NoSecurityChanges`アプリケーション ドメイン マネージャー、<xref:System.InvalidOperationException>が、アプリケーション ドメインのセキュリティを変更するあらゆる試みが行われた場合にスローされます。  
  
 呼び出す、 [iclrcontrol::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)はメソッドを呼び出すことと同じ`ICLRDomainManager::SetAppDomainManagerType`で`eInitializeNewDomainFlags_None`です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRDomainManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [EInitializeNewDomainFlags 列挙型](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
