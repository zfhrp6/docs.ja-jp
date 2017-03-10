---
title: "/preferreduilang (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/preferreduilang"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "preferreduilang compiler option [C#]"
  - "/preferreduilang compiler option [C#]"
  - "-preferreduilang compiler option [C#]"
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /preferreduilang (C# Compiler Options)
`/preferreduilang` コンパイラ オプションを使用すると、C\# コンパイラが出力を表示するエラー メッセージなどの言語を指定できます。  
  
## 構文  
  
```  
/preferreduilang: language  
```  
  
## Arguments  
 `language`  
 [言語名](http://go.microsoft.com/fwlink/p/?LinkId=236992) コンパイラ出力に使用する言語をクリックします。  
  
## 解説  
 C\# コンパイラのエラー メッセージ、およびそのほかのコマンド ラインの出力に使用する言語を指定します `/preferreduilang` のコンパイラ オプションを使用できます。  言語の言語パックがインストールされていない場合、オペレーティング システムの言語設定が使用され、エラーは報告されません。  
  
```c#  
csc.exe /preferreduilang:ja-JP  
```  
  
## 必要条件  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)