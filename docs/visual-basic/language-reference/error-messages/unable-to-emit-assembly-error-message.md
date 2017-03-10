---
title: "Unable to emit assembly: &lt;error message&gt; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30145"
  - "bc30145"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30145"
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Unable to emit assembly: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー \(Al.exe、Alink とも呼ばれます\) を呼び出しますが、アセンブリを生成する出力段階でリンカーからエラーが報告されます。  
  
 **Error ID:** BC30145  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを調べ、トピック「[Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/ja-jp/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)」でより詳細な説明とアドバイスを参照します。  
  
2.  [Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md) または [Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) を使用して、手動でのアセンブリへの署名を試みます。  
  
3.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
### アセンブリを手動で署名するには  
  
1.  [Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) を使用して、公開キーと秘密キーの一対のファイルを作成します。  
  
     このファイルは .snk の拡張子を持ちます。  
  
2.  エラーが発生している COM 参照をプロジェクトから削除します。  
  
3.  Windows の **\[スタート\]** ボタンをクリックし、**\[プログラム\]** をポイントします。次に **\[Microsoft Visual Studio 2008\]** をポイントし、**\[Visual Studio Tools\]** をポイントして、**\[Visual Studio 2008 コマンド プロンプト\]** をクリックします。  
  
4.  アセンブリ ラッパーを格納するディレクトリに移動します。  
  
5.  次のコードを入力します。  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     コードの一例として、次のように入力することができます。  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     パスやファイルに空白が含まれている場合には、二重引用符 \("\) を使用します。  
  
6.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で、作成したファイルに .NET アセンブリへの参照を追加します。  
  
## 参照  
 [Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/ja-jp/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)   
 [方法 : 公開キーと秘密キーのキー ペアを作成する](../Topic/How%20to:%20Create%20a%20Public-Private%20Key%20Pair.md)   
 [ご意見](/visual-studio/ide/talk-to-us)