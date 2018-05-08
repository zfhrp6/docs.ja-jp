---
title: EClrOperation 列挙型
ms.date: 03/30/2017
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b18c89cee0c3f5088a9978e448a0d61de1b9848
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="eclroperation-enumeration"></a>EClrOperation 列挙型
一連のホストがポリシーのアクションを適用できる操作について説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|ホストは、ときに実行されるポリシーのアクションを指定できます、<xref:System.AppDomain>正常でない (rude) 方式でモジュールはアンロードされます。|  
|`OPR_AppDomainUnload`|ホストは、ときに実行されるポリシーのアクションを指定できます、<xref:System.AppDomain>が読み込まれていません。|  
|`OPR_FinalizerRun`|ホストは、ファイナライザーを実行するときのポリシーのアクションを指定できます。|  
|`OPR_ProcessExit`|ホストは、ポリシー、プロセスが終了したときに実行されるアクションを指定できます。|  
|`OPR_ThreadAbort`|ホストは、スレッドが中止されたときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ThreadRudeAbortInCriticalRegion`|ホストは、コードの重要な領域で rude スレッドの中断が発生したときに実行されるポリシーのアクションを指定できます。|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|ホストは、重大でないコード領域で rude スレッドの中断が発生したときに実行されるポリシーのアクションを指定できます。|  
  
## <a name="remarks"></a>コメント  
 共通言語ランタイム (CLR) の信頼性インフラストラクチャは、中止とリソース内のコードとコードの重要ではない領域で発生した重要な領域の割り当てエラーを区別します。 この区別は、ホストのコードに障害が発生した場所に応じて異なるポリシーを設定できるように設計されています。  
  
 A*コードの重要な領域*は、CLR がそのタスクの中止またはリソースが現在のタスクだけに影響するために、要求を完了に失敗を保証できない領域。 たとえば、タスクは、ロックが保持していると、メモリ割り当て要求の発行時に失敗を示す HRESULT を受け取る場合、にないの安定性を確保するには、そのタスクを中止するだけでは不十分、<xref:System.AppDomain>であるため、<xref:System.AppDomain>他を含めることがありますタスクが同じロックを待機します。 現在を破棄する可能性がありますタスクがタスクのその他の応答を停止 (ハング) に無期限にします。 このような場合は、全体にアンロードする機能、ホストする必要があります。<xref:System.AppDomain>リスクの潜在的なが不安定になるのではなくです。  
  
 A*重大でないコード領域*、その一方で、CLR が、中断や障害の影響は、エラーが発生しているタスクのみれることを保証できる領域がします。  
  
 CLR も区別正常かつ非正常 (rude) 中止します。 一般に、正常または適切な中止は、あらゆる努力 rude 中止がこのような保証を行いません中にタスクを中止する前に、例外処理ルーチンで、ファイナライザーを実行します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [EClrFailure 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction 列挙型](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
