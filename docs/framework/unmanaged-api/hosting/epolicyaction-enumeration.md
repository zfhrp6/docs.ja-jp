---
title: EPolicyAction 列挙型
ms.date: 03/30/2017
api_name:
- EPolicyAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EPolicyAction
helpviewer_keywords:
- EPolicyAction enumeration [.NET Framework hosting]
ms.assetid: 72dd76ba-239e-45ac-9ded-318fb07d6c6d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14908ae641c8539659e6014deb2c5f35a6d1cfbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433631"
---
# <a name="epolicyaction-enumeration"></a>EPolicyAction 列挙型
ホストが記載された操作を設定できますポリシー操作について説明します[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)とによって記述されたエラー [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eNoAction,  
    eThrowException,  
    eAbortThread,  
    eRudeAbortThread,  
    eUnloadAppDomain,  
    eRudeUnloadAppDomain,  
    eExitProcess,  
    eFastExitProcess,  
    eRudeExitProcess,  
    eDisableRuntime  
} EPolicyAction;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAbortThread`|共通言語ランタイム (CLR) が、スレッドを適切に中止する必要がありますを指定します。 正常な中止では、すべてを実行する試行`finally`ブロックする場合に、いずれかの`catch`ブロックおよび関連するスレッドの中止、ファイナライザーを使用します。|  
|`eDisableRuntime`|CLR が無効な状態を入力する必要がありますを指定します。 マネージ コードを実行して、影響を受けるプロセスでそれ以上し、スレッドは CLR に入るをブロックします。|  
|`eExitProcess`|CLR がファイナライザーを実行して、クリーンアップ、およびログ記録操作など、プロセスの通常終了を試みる必要がありますを指定します。|  
|`eFastExitProcess`|CLR しないで終了すること、プロセス、すぐにファイナライザーを実行するか、クリーンアップ、およびログ記録操作を指定します。 ただし、デバッガーに通知が送信されます。|  
|`eNoAction`|アクションを実行しないことを指定します。|  
|`eRudeAbortThread`|CLR が rude スレッドの中止を実行する必要がありますを指定します。 のみ`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。|  
|`eRudeExitProcess`|CLR がファイナライザーを実行するか、操作のログ記録しないでプロセスを終了することを指定します。|  
|`eRudeUnloadAppDomain`|CLR がの rude アンロードを実行する必要がありますを指定、<xref:System.AppDomain>です。 マークされた唯一のファイナライザー<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。 これと同様に、すべてのスレッド<xref:System.AppDomain>スタックに表示される、 `ThreadAbortException`、だけが`catch`と`finally`でマークされたブロック<xref:System.EnterpriseServices.MustRunInClientContextAttribute>実行されます。|  
|`eThrowException`|メモリ不足、バッファーのオーバーフローなどの条件に該当する例外をスローすることを指定します。|  
|`eUnloadAppDomain`|指定する、<xref:System.AppDomain>がアンロードされます。 CLR は、ファイナライザーを実行しようとします。|  
  
## <a name="remarks"></a>コメント  
 ホストでは、ポリシーのアクションを設定のメソッドを呼び出すことによって、 [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)インターフェイスです。 中止されて rude かつ安全な方法については、次を参照してください。、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)列挙します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [EClrFailure 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
