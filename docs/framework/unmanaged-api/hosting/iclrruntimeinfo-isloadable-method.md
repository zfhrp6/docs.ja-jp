---
title: ICLRRuntimeInfo::IsLoadable メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432961"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable メソッド
このインターフェイスに関連付けられているランタイムを考慮に入れて、現在のプロセスに読み込めるかどうかを示す他のランタイムをプロセスに既に読み込まれている可能性があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbLoadable`  
 [out]`true` 、現在のプロセスに読み込まれます。 それ以外の場合、このランタイムができた場合`false`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pbLoadable` が null です。|  
  
## <a name="remarks"></a>コメント  
 別のランタイムが既にプロセスに読み込まれていて、インプロセスのサイド バイ サイド実行でこのインターフェイスに関連付けられているランタイムを読み込むことができます`pbLoadable`返します`true`です。 2 つのランタイムはサイド バイ サイドでプロセスを実行できない場合`pbLoadable`返します`false`です。 たとえば、共通言語ランタイム (CLR) バージョン 4 では、サイド バイ サイド CLR バージョン 2.0 を使用して同じプロセス内または CLR バージョン 1.1 を実行できます。 ただし、CLR バージョン 1.1 および CLR バージョン 2.0 では、サイド バイ サイドでプロセスを実行できません。  
  
 かどうかに、プロセスのランタイムは読み込まれません、このメソッドは常`true`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRRuntimeInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
