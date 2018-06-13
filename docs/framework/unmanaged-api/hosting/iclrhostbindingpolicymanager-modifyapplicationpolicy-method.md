---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a221b286ada97c3c03387556cb30ee6ddd2c453
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436255"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
指定したアセンブリのバインディング ポリシーを変更し、新しいバージョンのポリシーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzSourceAssemblyIdentity`  
 [in]変更するアセンブリの id。  
  
 `pwzTargetAssemblyIdentity`  
 [in]変更後のアセンブリの新しい id。  
  
 `pbApplicationPolicy`  
 [in]変更するアセンブリのバインディング ポリシー データを格納するバッファーへのポインター。  
  
 `cbAppPolicySize`  
 [in]置き換えられるバインディング ポリシーのサイズ。  
  
 `dwPolicyModifyFlags`  
 [in]論理 OR の組み合わせの[EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)リダイレクトのコントロールを示す値。  
  
 `pbNewApplicationPolicy`  
 [out]新しいデータのバインディング ポリシーを格納するバッファーへのポインター。  
  
 `pcbNewAppPolicySize`  
 [入力、出力].新しいバインド ポリシー バッファーのサイズへのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|ポリシーは正常に変更されました。|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` または`pwzTargetAssemblyIdentity`が null 参照でした。|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` が小さすぎます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR はプロセス内で使用可能ではなくなりました。 メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 `ModifyApplicationPolicy`メソッドを 2 回呼び出すことができます。 最初の呼び出しは、null 値を指定する必要があります、`pbNewApplicationPolicy`パラメーター。 この呼び出しのために必要な値が返さ`pcbNewAppPolicySize`です。 2 つ目の呼び出しは、のこの値を指定する必要があります`pcbNewAppPolicySize`の特定のサイズのバッファーを指す`pbNewApplicationPolicy`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRHostBindingPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
