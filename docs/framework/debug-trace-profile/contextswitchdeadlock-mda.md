---
title: "contextSwitchDeadlock MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "deadlocks [.NET Framework]"
  - "pumping messages"
  - "STA message pumping"
  - "single-threaded COM components"
  - "MDAs (managed debugging assistants), context switching deadlocks"
  - "managed debugging assistants (MDAs), context switching deadlocks"
  - "ContextSwitchDeadlock MDA"
  - "message pumping"
  - "context switching deadlocks"
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 22
---
# contextSwitchDeadlock MDA
`contextSwitchDeadlock` マネージ デバッグ アシスタント \(MDA\) は、COM コンテキストの遷移の試行中にデッドロックが検出されるとアクティブ化されます。  
  
## 症状  
 最も一般的な症状は、マネージ コードから実行されたアンマネージ COM コンポーネントの呼び出しから戻らないことです。  別の症状として、メモリの使用量が時間と共に増加する場合もあります。  
  
## 原因  
 最も考えられる原因として、シングルスレッド アパートメント \(STA\) スレッドがメッセージ ポンプを行っていないことがあります。  STA スレッドが、メッセージ ポンプを行わずに待機しているか、または時間のかかる操作を実行していて、メッセージ キューのポンプを許可していません。  
  
 メモリ使用量が時間の経過と共に増加する症状は、ファイナライザー スレッドがアンマネージ COM コンポーネント上の `Release` を呼び出そうとして、そのコンポーネントが戻らない場合に発生します。  このため、ファイナライザーは他のオブジェクトを再利用できなくなります。  
  
 既定では、Visual Basic コンソール アプリケーションのメイン スレッドのスレッド処理モデルは STA です。  STA スレッドが共通言語ランタイムまたはサードパーティ コントロールを通じて COM 相互運用性を直接または間接的に使用する場合、この MDA がアクティブ化されます。  Visual Basic コンソール アプリケーションでこの MDA がアクティブ化されるのを防ぐには、メイン メソッドに <xref:System.MTAThreadAttribute> 属性を適用するか、またはメッセージをポンプするようにアプリケーションを変更します。  
  
 次のすべての条件が満たされる場合、この MDA が誤ってアクティブ化される可能性があります。  
  
-   アプリケーションがライブラリを通じて直接または間接的に STA スレッドから COM コンポーネントを作成する。  
  
-   デバッガーでアプリケーションが中断され、ユーザーがアプリケーションを続行したか、またはステップ操作を実行した。  
  
-   アンマネージ デバッグが有効になっていない。  
  
 MDA が誤ってアクティブ化されたかどうかを判断するには、すべてのブレークポイントを無効にし、アプリケーションを再び実行して、中断なしで実行させます。  MDA がアクティブ化されない場合は、最初のアクティブ化は誤りだった可能性があります。  その場合は、MDA を無効にして、デバッグ セッションとの干渉を防ぎます。  
  
> [!NOTE]
>  この MDA は、[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 以上のバージョンの既定のセットに含まれています。  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でホスティング プロセスが有効にされている場合、既定のセットに含まれる MDA を無効にすることはできません。  ホスティング プロセスは既定で有効になるため、明示的に無効にする必要があります。  MDA を無効にする方法については、「[Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)」の「MDA の有効化と無効化」を参照してください。  
  
## 解像度  
 STA メッセージ ポンプに関する COM 規則に従います。  
  
## ランタイムへの影響  
 この MDA は CLR に影響しません。  COM コンテキストに関するデータを報告するだけです。  
  
## 出力  
 現在のコンテキストおよびターゲット コンテキストを説明するメッセージです。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)