---
title: ICLRMetaHost::ExitProcess メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.ExitProcess
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::ExitProcess
helpviewer_keywords:
- ICLRMetaHost::ExitProcess method [.NET Framework hosting]
- ExitProcess method, ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: b4df98cc-4e4e-407b-b8f4-e0076afef3a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc71762fb4a660cf84814cdd46d09696a161f3c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431598"
---
# <a name="iclrmetahostexitprocess-method"></a>ICLRMetaHost::ExitProcess メソッド
正常に読み込まれているすべてのランタイムをシャット ダウンしようとして、プロセスを終了します。 置き換えるソフトウェア更新プログラム、 [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ExitProcess (  
    [in] INT32 iExitCode);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iExitCode`  
 [in]プロセスの終了コード。  
  
## <a name="return-value"></a>戻り値  
 このメソッドに値が戻りませんため、その戻り値が定義されていません。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRMetaHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
