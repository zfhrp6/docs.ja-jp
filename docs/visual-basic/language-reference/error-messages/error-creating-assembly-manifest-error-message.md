---
title: "Error creating assembly manifest: &lt;error message&gt; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30140"
  - "vbc30140"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30140"
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# Error creating assembly manifest: &lt;error message&gt;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラはアセンブリ リンカー \(Al.exe、Alink とも呼ばれる\) を呼び出し、マニフェストを伴うアセンブリを生成します。  リンカーが、アセンブリの生成前の段階でのエラーを報告しています。  
  
 指定したキー ファイルまたはキー コンテナーに原因がある場合があります。  アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。  アセンブリに遅延署名するには、**\[遅延署名のみ\]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。  アセンブリに遅延署名する場合、秘密キーは必要ありません。  詳細については、「[How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/f468a7d3-234c-4353-924d-8e0ae5896564)」を参照してください。  
  
 **Error ID:** BC30140  
  
### このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを調べ、エラー AL1019 に関するトピック「[Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/ja-jp/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)」でより詳細な説明とアドバイスを参照します。  
  
2.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
## 参照  
 [How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [\[署名\] ページ \(プロジェクト デザイナー\)](/visual-studio/ide/reference/signing-page-project-designer)   
 [Al.exe \(アセンブリ リンカー\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)   
 [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/ja-jp/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [ご意見](/visual-studio/ide/talk-to-us)