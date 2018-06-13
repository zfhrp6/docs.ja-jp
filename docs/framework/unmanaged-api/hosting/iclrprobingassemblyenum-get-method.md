---
title: ICLRProbingAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f5ddd352d027365e02366e9aa779053da3bdc2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434805"
---
# <a name="iclrprobingassemblyenumget-method"></a>ICLRProbingAssemblyEnum::Get メソッド
指定したインデックス位置には、アセンブリの id を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwIndex`  
 [in]アセンブリ id を返すの 0 から始まるインデックス。  
  
 `pwzBuffer`  
 [out]アセンブリの id データを格納しているバッファー。  
  
 `pcchBufferSize`  
 [入力、出力].サイズ、`pwzBuffer`バッファー。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`Get` 正常に返されます。|  
|ERROR_INSUFFICIENT_BUFFER|`pwzBuffer` が小さすぎます。|  
|ERROR_NO_MORE_ITEMS|列挙には、これ以上項目が含まれています。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元は、ロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。 ホスティング メソッドが存在する後続の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。|  
  
## <a name="remarks"></a>コメント  
 インデックス 0 の id は、プロセッサ アーキテクチャに固有の id です。 インデックス 1 の id は、Microsoft intermediate language (MSIL) のアーキテクチャに依存しないアセンブリです。 インデックス 2 の id には、アーキテクチャの情報が含まれていません。  
  
 `Get` 通常 2 回呼び出されます。 最初の呼び出しに対して null 値を提供する`pwzBuffer`、設定と`pcchBufferSize`の適切なサイズに`pwzBuffer`です。 2 番目の呼び出しを適切なサイズ指定`pwzBuffer`、完了したときに標準アセンブリの id データが含まれています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRProbingAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
