---
title: "Exceptions in Managed Threads | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unhandled exceptions,in managed threads"
  - "threading [.NET Framework],unhandled exceptions"
  - "threading [.NET Framework],exceptions in managed threads"
  - "managed threading"
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Exceptions in Managed Threads
.NET Framework のバージョン 2.0 以降では、共通言語ランタイムはスレッド内のほとんどの未処理の例外をそのまま続行させます。  ほとんどの場合、これは未処理の例外によってアプリケーションが終了することを意味します。  
  
> [!NOTE]
>  これは、スレッド プールのスレッド内での未処理の例外など、多数の未処理の例外に関する安全策を提供している、.NET Framework Version 1.0 および 1.1 からの重要な変更です。  このトピックの「[以前のバージョンからの変更](#ChangeFromPreviousVersions)」を参照してください。  
  
 共通言語ランタイムには、プログラム フローの制御に使用する特定の未処理の例外について、次のような安全策が用意されています。  
  
-   <xref:System.Threading.Thread.Abort%2A> が呼び出されると、スレッドで <xref:System.Threading.ThreadAbortException> がスローされる。  
  
-   スレッドが実行中のアプリケーション ドメインがアンロードされると、スレッドで <xref:System.AppDomainUnloadedException> がスローされます。  
  
-   共通言語ランタイムまたはホスト プロセスは、内部例外をスローすることによってスレッドを終了します。  
  
 共通言語ランタイムによって作成されたスレッドでこれらの例外が処理されない場合、その例外によってスレッドは終了しますが、共通言語ランタイムは例外を続行させません。  
  
 メイン スレッドまたはアンマネージ コードからランタイムに入ったスレッドでこれらの例外が処理されない場合、例外は通常どおり続行するため、アプリケーションが終了します。  
  
> [!NOTE]
>  マネージ コードが例外ハンドラーをインストールする機会を得る前に、ランタイムは未処理の例外をスローできます。  マネージ コードにこのような例外を処理する機会がない場合でも、例外を続行させることができます。  
  
## 開発時におけるスレッド処理の問題の露呈  
 アプリケーションを終了せずに、スレッドが暗黙に失敗したまま放置されていると、プログラミングの深刻な問題が検出されない状態になる可能性があります。  長期間実行されるサービスや他のアプリケーションでは、これは特に問題となります。  スレッドが失敗すると、プログラムの状態が徐々に破損します。  アプリケーションのパフォーマンスが低下する場合もあれば、アプリケーションがハングする場合もあります。  
  
 スレッド内で未処理の例外を続行させておき、結果としてオペレーティング システムにそのプログラムを終了させることで、開発およびテスト中にこのような問題が明らかになります。  プログラムの終了に関するエラー報告はデバッグをサポートします。  
  
<a name="ChangeFromPreviousVersions"></a>   
## 以前のバージョンからの変更  
 最も重要な変更は、マネージ スレッドに関する変更です。  .NET Framework Version 1.0 および 1.1 では、共通言語ランタイムには、次の状況での未処理の例外に関する安全策が用意されています。  
  
-   スレッド プールのスレッドの未処理の例外は存在しません。  タスクが例外をスローし、その例外が処理されない場合、ランタイムは例外のスタック トレースをコンソールに出力し、スレッドをスレッド プールに戻します。  
  
-   <xref:System.Threading.Thread> クラスの <xref:System.Threading.Thread.Start%2A> メソッドで作成されたスレッドの未処理の例外は存在しません。  このようなスレッド上で実行中のコードが例外をスローし、その例外が処理されない場合、ランタイムは例外のスタック トレースをコンソールに出力し、スレッドを適切に終了します。  
  
-   ファイナライザー スレッドの未処理の例外は存在しません。  ファイナライザーが例外をスローし、その例外が処理されない場合、ランタイムは例外のスタック トレースをコンソールに出力し、ファイナライザー スレッドがファイナライザーの実行を再開できるようにします。  
  
 マネージ スレッドのフォアグラウンドまたはバックグラウンドのステータスは、この動作に影響しません。  
  
 アンマネージ コードで作成されたスレッドの未処理の例外の場合、微妙な相違点があります。  ランタイムの JIT アタッチ ダイアログは、ネイティブ コードを通ってきたスレッド内でのマネージ例外またはネイティブ例外に関する、オペレーティング システム ダイアログより優先されます。  プロセスは常に終了します。  
  
### コードの移行  
 通常は、この変更によってこれまでに認識されていないプログラミングの問題が明らかになるため、問題を修正できます。  ただし、プログラマがランタイムの安全策 \(スレッドを終了するなど\) を利用する場合もあります。  状況によっては、プログラマは次の移行方法のいずれかを検討する必要があります。  
  
-   シグナルを受信したときに、スレッドが適切に終了するようにコードを再構築します。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> メソッドを使用して、スレッドを中止します。  
  
-   プロセスを終了できるように、スレッドを中止する必要がある場合は、スレッドをバックグラウンド スレッドにして、プロセス終了時にスレッドが自動的に終了するようにします。  
  
 どのような場合でも、方法は例外に関するデザイン ガイドラインに従う必要があります。  「[例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)」を参照してください。  
  
### アプリケーション互換性フラグ  
 一時的な互換性対策として、管理者はアプリケーション構成ファイルの `<runtime>` セクションに互換性フラグを配置できます。  これにより、共通言語ランタイムを Version 1.0 および 1.1 の動作に戻すことができます。  
  
```  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## ホストのオーバーライド  
 .NET Framework Version 2.0 では、アンマネージ ホストはホスト API の [ICLRPolicyManager](../../../ocs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) インターフェイスを使用して、共通言語ランタイムの既定の未処理の例外ポリシーをオーバーライドできます。  [ICLRPolicyManager::SetUnhandledExceptionPolicy](../Topic/ICLRPolicyManager::SetUnhandledExceptionPolicy%20Method.md) 関数を使用して、未処理の例外のポリシーを設定します。  
  
## 参照  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)