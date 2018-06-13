---
title: MDAInfo 構造体
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5164e85ecc97de99dcc493c2ba5efa8fc3468471
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443181"
---
# <a name="mdainfo-structure"></a>MDAInfo 構造体
詳細について説明、`Event_MDAFired`マネージ デバッグ アシスタント (MDA) の作成をトリガーするイベントです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`lpMDACaption`|現在の MDA のタイトル。 タイトルを引き起こしたエラーの種類を記述する、`Event_MDAFired`イベント。|  
|`lpMDAMessage`|現在の MDA によって提供される出力メッセージです。|  
  
## <a name="remarks"></a>コメント  
 マネージ デバッグ アシスタント (Mda) がデバッグでランタイム実行エンジンは、共通言語ランタイム (CLR) で無効な条件を識別するなどのタスクを実行すると連携して動作する支援またはの状態に関する追加情報をダンプしますエンジン。 Mda は、それ以外の場合トラップが難しいイベントに関する XML メッセージを生成します。 マネージ コードとアンマネージ コード間の遷移のデバッグに特に役立つは。  
  
 MDA の作成をトリガーするイベントが発生したときに、ランタイムは、次の手順を受け取ります。  
  
-   ホストが登録されていない場合、 [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)を呼び出してインスタンス[iclroneventmanager::registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)の通知を受信する、`Event_MDAFired`イベント、ランタイム処理を実行、既定値は、ホストなしの動作です。  
  
-   ホストがこのイベントのハンドラーを登録済みの場合、ランタイムは、デバッガーがプロセスにアタッチされているかどうかを確認します。 場合は、ランタイムはデバッガーを中断します。 デバッガーが引き続き発生する場合は、ホストを呼び出します。 デバッガーがアタッチされていない場合、ランタイムが呼び出す`IActionOnCLREvent::OnEvent`へのポインターを渡すと、`MDAInfo`インスタンスとして、`data`パラメーター。  
  
 Mda をアクティブ化して、MDA がアクティブ化されたときに通知するホストを選択できます。 これにより、ホストは、営業案件を既定の動作をオーバーライドして、プロセス状態が破損を防ぐため、イベントを発生させたマネージ スレッドを中止します。 Mda の使用に関する詳細については、次を参照してください。[マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
