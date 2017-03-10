---
title: "An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_CantGetMemoryMappedFile"
dev_langs: 
  - "VB"
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アプリケーションは、必要なオペレーティング システムのリソースを取得できませんでした。  この問題の考えられる原因の一部は次のとおりです。  
  
-   指定されたオペレーティング システム オブジェクトを作成するためのアクセス許可がアプリケーションにない。  
  
-   メモリ マップト ファイルを作成するためのアクセス許可が共通言語ランタイムにない。  
  
-   アプリケーションからオペレーティング システム オブジェクトにアクセスする必要があるが、別のプロセスがそれを使用している。  
  
### このエラーを解決するには  
  
1.  指定されたオペレーティング システム オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
2.  メモリ マップト ファイルを作成するための十分なアクセス許可が共通言語ランタイムにあることを確認します。  
  
3.  コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
4.  エラーが発生した状況を記録して、マイクロソフト プロダクト サポート サービスにご連絡ください。  
  
## 参照  
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [デバッガーの基本事項](/visual-studio/debugger/debugger-basics)   
 [ご意見](/visual-studio/ide/talk-to-us)