---
title: "streamWriterBufferedDataLost MDA | Microsoft Docs"
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
  - "StreamWriter class, data buffering problems"
  - "managed debugging assistants (MDAs), StreamWriter data buffering"
  - "buffers, StreamWriter problems"
  - "MDAs (managed debugging assistants), StreamWriter data buffering"
  - "StreamWriter buffered data lost"
  - "data buffering problems"
  - "streamWriterBufferedDataLost MDA"
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# streamWriterBufferedDataLost MDA
`streamWriterBufferedDataLost` マネージ デバッグ アシスタント \(MDA\) は、<xref:System.IO.StreamWriter> に書き込まれても、その後、<xref:System.IO.StreamWriter> のインスタンスが破棄される前に <xref:System.IO.StreamWriter.Flush%2A> メソッドや <xref:System.IO.StreamWriter.Close%2A> メソッドが呼び出されないときにアクティブになります。  この MDA を有効にすると、ランタイムは、<xref:System.IO.StreamWriter> 内にバッファー データが存在しているかどうかを確認します。  バッファー データが存在する場合、MDA はアクティブになります。  <xref:System.GC.Collect%2A> メソッドや <xref:System.GC.WaitForPendingFinalizers%2A> メソッドを呼び出すと、ファイナライザーを強制的に実行できます。  ファイナライザーは、これ以外では任意の時点で動作し、プロセス終了時に動作する可能性はありません。  この MDA を有効にしてファイナライザーを明示的に実行すると、この種の問題をより確実に再現できるようになります。  
  
## 症状  
 <xref:System.IO.StreamWriter> は、最後の 1 ～ 4 KB のデータをファイルに書き込みません。  
  
## 原因  
 <xref:System.IO.StreamWriter> はデータを内部にバッファリングします。この場合、<xref:System.IO.StreamWriter.Close%2A> メソッドまたは <xref:System.IO.StreamWriter.Flush%2A> メソッドを呼び出して、バッファー データを基になるデータ ストアに書き込む必要があります。  <xref:System.IO.StreamWriter.Close%2A> や <xref:System.IO.StreamWriter.Flush%2A> が適切に呼び出されなかった場合、<xref:System.IO.StreamWriter> インスタンスにバッファリングされたデータが正しく書き込まれないことがあります。  
  
 この MDA がキャッチする、記述が不適切なコード例を次に示します。  
  
```  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 上のコードでは、ガベージ コレクションがトリガーされ、ファイナライザーが終了するまで中断された場合、この MDA がより確実にアクティブになります。  この種の問題を追跡するには、デバッグ ビルドで前のメソッドの末尾に次のコードを追加します。  これにより、MDA は確実にアクティブになりますが、問題の原因が解決されるというわけではありません。  
  
```  
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## 解決策  
 <xref:System.IO.StreamWriter> のインスタンスを持つアプリケーションまたはコード ブロックを閉じる前に、<xref:System.IO.StreamWriter> で <xref:System.IO.StreamWriter.Close%2A> または <xref:System.IO.StreamWriter.Flush%2A> を呼び出します。  これを実現する最良の機構の 1 つが、C\# の `using` ブロック \(Visual Basic の場合は `Using`\) を使用してインスタンスを作成することです。これにより、ライターの <xref:System.IO.StreamWriter.Dispose%2A> メソッドが呼び出され、その結果、インスタンスが正しく閉じられます。  
  
```  
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 `using` の代わりに `try/finally` を使用した同様の解決策を次のコードに示します。  
  
```  
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 これらの解決策のいずれも使用できない場合 \(たとえば、<xref:System.IO.StreamWriter> が静的変数に格納され、その有効期間の最後にコードを簡単に実行できない場合など\)、<xref:System.IO.StreamWriter> を最後に使用した後に <xref:System.IO.StreamWriter.Flush%2A> を呼び出すか、または最初に使用する前に <xref:System.IO.StreamWriter.AutoFlush%2A> プロパティを `true` に設定すると、この問題を回避できます。  
  
```  
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## ランタイムへの影響  
 この MDA は、ランタイムに影響しません。  
  
## 出力  
 この違反が発生したことを示すメッセージ  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.IO.StreamWriter>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)