---
title: ICLRMetaHost::GetRuntime メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c83f6dfe069b75f1ab3256f4e5a083f85b50adad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435917"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime メソッド
取得、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)共通言語ランタイム (CLR) の特定のバージョンに対応するインターフェイスです。 このメソッドは、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)で使用される関数、 [STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)フラグ。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in, REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzVersion`  
 [in]形式で、メタデータに格納されている .NET Framework のコンパイル バージョン"v*A*.*B*[.*X*]"です。 *A*、 *B*、および*X*はメジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数。  
  
> [!NOTE]
>  このパラメーターは、C:\Windows\Microsoft.NET\Framework または C:\Windows\Microsoft.NET\Framework64 で表示される、.NET Framework のバージョンのディレクトリ名と一致する必要があります。  
  
 値の例は、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"および"v4.0 です。*X*"ここで、 *X*インストールされているビルドの数によって異なります。 "V"プレフィックスが必要です。  
  
 `riid`  
 [in]目的のインターフェイスの識別子です。 現時点では、このパラメーターの唯一の有効な値は、IID_ICLRRuntimeInfo がします。  
  
 `ppRuntime`  
 [out]ポインター、 [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)要求されたランタイムに対応するインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzVersion` または `ppRuntime` が null です。|  
  
## <a name="remarks"></a>コメント  
 このメソッドが対話一貫して従来のインターフェイスなど、 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)インターフェイスおよび従来の機能など、非推奨`CorBindTo*`関数 (を参照してください[廃止 CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) API をホストしている .NET Framework 2.0 で)。 従来の API が読み込まれているランタイムは、新しい API を表示でき、新しい API が読み込まれているランタイムがレガシ API に表示されます。 である必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 
  [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
