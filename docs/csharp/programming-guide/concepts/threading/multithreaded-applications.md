---
title: "マルチスレッド アプリケーション (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: b7015cfb-d506-4eac-b2f8-b2caaa9cc977
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a36fd71ff41eb219f4c4de36d4fa8da9b8ee179a
ms.lasthandoff: 03/13/2017

---
# <a name="multithreaded-applications-c"></a>マルチスレッド アプリケーション (C#)
C# では、複数のタスクを同時に実行するアプリケーションを記述できます。 他のタスクを止める可能性があるタスクは個別のスレッドで実行できます。これは*マルチスレッド*や*フリー スレッド*と呼ばれているプロセスです。  
  
 マルチスレッドを利用するアプリケーションはユーザーの入力に対する応答性が良くなります。プロセッサを集中的に利用するタスクが個別のスレッドで実行されるため、ユーザー インターフェイスの動作が妨げられません。 マルチスレッドはまた、スケーラブルなアプリケーションの開発にも便利です。ワークロードが増えたとき、スレッドを追加できるからです。  
  
## <a name="creating-and-using-threads"></a>スレッドを作成し、使用する  
 アプリケーションのスレッドの動作をさらに細かく制御するには、スレッドを自分で管理します。 しかしながら、正しく機能するマルチスレッド アプリケーションは記述が難しいことを知ってください。競合状態になり、応答が停止したり、一時的なエラーが発生したりすることがあります。 詳しくは、「[スレッドセーフ コンポーネント](http://msdn.microsoft.com/library/4f7c7377-a782-4bd0-aaa3-9db8c12945ee)」を参照してください。  
  
 新しいスレッドを作成します。<xref:System.Threading.Thread> 型の変数を宣言し、コンストラクターを呼び出し、新しいスレッドで実行するプロシージャまたはメソッドの名前を指定します。 次にコード例を示します。  
  
```csharp  
System.Threading.Thread newThread =  
    new System.Threading.Thread(AMethod);  
```  
  
### <a name="starting-and-stopping-threads"></a>スレッドの開始と停止  
 新しいスレッドの実行を開始するには、次のコードにあるように、<xref:System.Threading.Thread.Start%2A> メソッドを使用します。  
  
```csharp  
newThread.Start();  
```  
  
 スレッドの実行を停止するには、次のコードにあるように、<xref:System.Threading.Thread.Abort%2A> メソッドを使用します。  
  
```csharp  
newThread.Abort();  
```  
  
 スレッドの開始と停止に加え、スレッドを中断することもできます。<xref:System.Threading.Thread.Sleep%2A> または <xref:System.Threading.Thread.Suspend%2A> を呼び出します。中断しているスレッドを再開するには、<xref:System.Threading.Thread.Resume%2A> メソッドを使用します。スレッドを破棄するには <xref:System.Threading.Thread.Abort%2A> メソッドを使用します。  
  
### <a name="thread-methods"></a>スレッド メソッド  
 次の表は、個々のスレッドを制御できるメソッドをまとめたものです。  
  
|メソッド|操作|  
|------------|------------|  
|<xref:System.Threading.Thread.Start%2A>|スレッドの実行を開始します。|  
|<xref:System.Threading.Thread.Sleep%2A>|指定した時間だけスレッドを一時停止します。|  
|<xref:System.Threading.Thread.Suspend%2A>|セーフ ポイントに到達するとスレッドを一時停止します。|  
|<xref:System.Threading.Thread.Abort%2A>|セーフ ポイントに到達するとスレッドを停止します。|  
|<xref:System.Threading.Thread.Resume%2A>|一時停止になっているスレッドを再開します。|  
|<xref:System.Threading.Thread.Join%2A>|別のスレッドが完了するまで現在のスレッドに待機させます。 タイムアウト値と併用すると、このメソッドは、割り当てられた時間でスレッドが完了した場合、`True` を返します。|  
  
### <a name="safe-points"></a>セーフ ポイント  
 以上のメソッドのほとんどは名前を見ればその機能が明らかですが、*セーフ ポイント*は初めて耳にする概念かもしれません。 セーフ ポイントとは、共通言語ランタイムが自動*ガベージ コレクション*を安全に実行できる (コード内の) 場所です。ガベージ コレクションは、未使用の変数とメモリを解放するプロセスです。 スレッドの <xref:System.Threading.Thread.Abort%2A> または <xref:System.Threading.Thread.Suspend%2A> メソッドを呼び出すと、共通言語ランタイムはコードを分析し、スレッドが実行を停止する場所を決定します。  
  
### <a name="thread-properties"></a>スレッド プロパティ  
 スレッドには、便利なプロパティもあります。次の表をご覧ください。  
  
|プロパティ|値|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|スレッドがアクティブな場合、値 `True` が含まれます。|  
|<xref:System.Threading.Thread.IsBackground%2A>|スレッドがバックグラウンド スレッドかどうか、あるいはバックグラウンド スレッドにする必要があるかどうかを示すブール値を取得または設定します。 バックグラウンド スレッドはフォアグラウンド スレッドに似ていますが、プロセスの停止を阻止しません。 あるプロセスに属するフォアグラウンド スレッドがすべて停止すると、共通言語ランタイムは、アライブ状態のバックグラウンド スレッドで <xref:System.Threading.Thread.Abort%2A> メソッドを呼び出し、プロセスを終了します。|  
|<xref:System.Threading.Thread.Name%2A>|スレッドの名前を取得または設定します。 デバッグ時、個々のスレッドを検出するために頻繁に使用されます。|  
|<xref:System.Threading.Thread.Priority%2A>|オペレーティング システムがスレッド スケジュールに優先順位を設定するために使用する値を取得または設定します。|  
|<xref:System.Threading.Thread.ThreadState%2A>|スレッドの状態を説明する値が含まれます。|  
  
## <a name="thread-priorities"></a>スレッドの優先順位  
 すべてのスレッドに優先順位が与えられます。その優先順位により、スレッドが実行するプロセッサのタイム スライスの大小が決定されます。 オペレーティング システムは、優先順位の高いスレッドに長いタイム スライスを割り当て、優先順位の低いスレッドに短いタイム スライスを割り当てます。 新しいスレッドは値 `Normal` で作成されますが、<xref:System.Threading.Thread.Priority%2A> プロパティを <xref:System.Threading.ThreadPriority> 列挙の任意の値に変更できます。  
  
 さまざまなスレッド優先順位の詳細については、「<xref:System.Threading.ThreadPriority>」を参照してください。  
  
## <a name="foreground-and-background-threads"></a>フォアグラウンド スレッドとバックグラウンド スレッド  
 *フォアグラウンド スレッド*は無期限で実行されます。*バックグラウンド スレッド*は、最後のフォアグラウンド スレッドが停止した直後に停止します。 <xref:System.Threading.Thread.IsBackground%2A> プロパティを利用し、スレッドのバックグラウンド状態を確認したり、変更したりできます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>   
 [スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [マルチスレッド プロシージャのパラメーターと戻り値 (C#)](../../../../csharp/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [スレッド処理 (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)
