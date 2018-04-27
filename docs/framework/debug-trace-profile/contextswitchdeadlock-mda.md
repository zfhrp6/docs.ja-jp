---
title: contextSwitchDeadlock MDA
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: 22
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f3ee9aef3bc824ee25e577a5dbd14aeaa210be3
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="contextswitchdeadlock-mda"></a>contextSwitchDeadlock MDA
`contextSwitchDeadlock` マネージ デバッグ アシスタント (MDA) は、COM コンテキストの遷移の試行中にデッドロックが検出されるとアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 最も一般的な症状は、マネージ コードから実行されたアンマネージ COM コンポーネントの呼び出しから戻らないことです。  別の症状として、メモリの使用量が時間と共に増加する場合もあります。  
  
## <a name="cause"></a>原因  
 最も考えられる原因として、シングルスレッド アパートメント (STA) スレッドがメッセージ ポンプを行っていないことがあります。 STA スレッドが、メッセージ ポンプを行わずに待機しているか、または時間のかかる操作を実行していて、メッセージ キューのポンプを許可していません。  
  
 メモリ使用量が時間の経過と共に増加する症状は、ファイナライザー スレッドがアンマネージ COM コンポーネント上の `Release` を呼び出そうとして、そのコンポーネントが戻らない場合に発生します。  このため、ファイナライザーは他のオブジェクトを再利用できなくなります。  
  
 既定では、Visual Basic コンソール アプリケーションのメイン スレッドのスレッド処理モデルは STA です。 STA スレッドが共通言語ランタイムまたはサードパーティ コントロールを通じて COM 相互運用性を直接または間接的に使用する場合、この MDA がアクティブ化されます。  Visual Basic コンソール アプリケーションでこの MDA がアクティブ化されるのを防ぐには、メイン メソッドに <xref:System.MTAThreadAttribute> 属性を適用するか、またはメッセージをポンプするようにアプリケーションを変更します。  
  
 次のすべての条件が満たされる場合、この MDA が誤ってアクティブ化される可能性があります。  
  
-   アプリケーションがライブラリを通じて直接または間接的に STA スレッドから COM コンポーネントを作成する。  
  
-   デバッガーでアプリケーションが中断され、ユーザーがアプリケーションを続行したか、またはステップ操作を実行した。  
  
-   アンマネージ デバッグが有効になっていない。  
  
 MDA が誤ってアクティブ化されたかどうかを判断するには、すべてのブレークポイントを無効にし、アプリケーションを再び実行して、中断なしで実行させます。 MDA がアクティブ化されない場合は、最初のアクティブ化は誤りだった可能性があります。 その場合は、MDA を無効にして、デバッグ セッションとの干渉を防ぎます。  
  
> [!NOTE]
>  この MDA は、[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 以上のバージョンの既定のセットに含まれています。 Visual Studio では、ホスト プロセスが有効の場合、既定で設定される Mda を無効にできません。 ホスティング プロセスは既定で有効になるため、明示的に無効にする必要があります。 MDA を無効にする方法については、「[マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」の「MDA の有効化と無効化」を参照してください。  
  
## <a name="resolution"></a>解像度  
 STA メッセージ ポンプに関する COM 規則に従います。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。 COM コンテキストに関するデータを報告するだけです。  
  
## <a name="output"></a>出力  
 現在のコンテキストおよびターゲット コンテキストを説明するメッセージです。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
