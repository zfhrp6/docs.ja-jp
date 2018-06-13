---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dcddb5766894a30f1ccb2552a09abe7153c6eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434953"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド
指定したマネージ アセンブリで、指定した型の指定したメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzAssemblyPath`  
 [in]パス、<xref:System.Reflection.Assembly>を定義する、<xref:System.Type>メソッドが呼び出される、します。  
  
 `pwzTypeName`  
 [in]名前、<xref:System.Type>に呼び出すメソッドを定義します。  
  
 `pwzMethodName`  
 [in]呼び出すメソッドの名前です。  
  
 `pwzArgument`  
 [in]メソッドに渡す文字列パラメーター。  
  
 `pReturnValue`  
 [out]呼び出されたメソッドで返される整数値。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドから E_FAIL が返された場合、CRL はプロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 呼び出されたメソッドは、次のシグネチャが必要です。  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 ここで`pwzMethodName`呼び出されたメソッドの名前を表すと`pwzArgument`そのメソッドにパラメーターとして渡される文字列値を表します。 S_OK HRESULT 値が設定されている場合`pReturnValue`が呼び出されたメソッドで返された整数値に設定します。 それ以外の場合、`pReturnValue`が設定されていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
